#task 1,2
def find_spamer(parsed_log):
    pass

    if not parsed_log:
        return None

    db = {}

    for log in  parsed_log:
        if not db.get(log[0]):
            db[log[0]] = {"count":1, "files":set([log[2]])}
        else:
            db[log[0]]["count"] += 1
            db[log[0]]["files"].add(log[2])

    return max(db.items(), key=lambda x: x[1]["count"])


if __name__ == "__main__":
   a = parse_log("./nginx_logs.txt")
   for e in a:
       print(e)
   parsed_log = parse_log("./nginx_logs.txt")
   spamer = find_spamer(parsed_log) 

#task 3,4
import json

from myutils import my_zip_gen


def groping(
        output_pth="./out.txt",
        user_pth="./users.csv",
        hobby_pth="./hobby.csv"):

    if not (user_pth or hobby_pth):
        return -1

    user_lines = None
    hobby_lines = None

    with open(user_pth, "r", encoding="utf-8") as user_file:
        user_lines = user_file.readlines()

    with open(hobby_pth, "r", encoding="utf-8") as hobby_file:
        hobby_lines = hobby_file.readlines()

    if len(user_lines) < len(hobby_lines):
        return 1

    group = {}

    for fio, hobby in my_zip_gen(user_lines, hobby_lines):
        fio = fio.replace("\n", "").replace(",", " ")
        group[fio] = hobby.replace("\n", "") if hobby else None

    with open(output_pth, "w+", encoding="utf-8") as out_file:
        out_file.writelines(json.dumps(group))
    


    return 0

