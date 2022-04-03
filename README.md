#1 Выяснить тип результата выражений
print(f"type(14 * 3) is {type(15 * 3)}")
print(f"type(15 / 3) is {type(15 / 3)}")
print(f"type(15 // 3) is {type(15 // 3)}")
print(f"type(15 ** 3) is {type(15 ** 3)}")

#2 Дан список:
input_list = ['в', '5', 'часов', '17', 'минут', 'температура', 'воздуха', 'была', '+5', 'градусов']
length_of_list:int = len(input_list)
store_id = id(input_list)

print(f"id before {store_id}")

for _ in range(length_of_list): # pyright change i to _

    elem = input_list.pop(0)

    if elem.isdigit() and elem.isalnum(): # no nessary use isalnum in here but I use
        input_list.append(f'"{int(elem):02d}"')
        # or   ['"', "00", '"']
        # input_list.append('"')
        # input_list.append(f'{int(elem):02d}')
        # input_list.append('"')


    elif elem[0] == "+" and elem[1].isdigit():
        input_list.append(f'"+{int(elem):02d}"')
        # or   ['"', "+00", '"']
        # input_list.append('"')
        # input_list.append(f'+{int(elem):02d}')
        # input_list.append('"')

    else:
        input_list.append(elem)

print(' '.join(input_list))

print(f"id after {id(input_list)}")

#4 Дан список, содержащий искажённые данные с должностями и именами сотрудников
input_list = ['инженер-конструктор Игорь',
            'главный бухгалтер МАРИНА',
            'токарь высшего разряда нИКОЛАй',
            'директор аэлита']
answer = {}

for string in input_list:
    correct_name = string.split()[-1].capitalize()
    print(f"Привет, {correct_name}!")

#5 Создать список, содержащий цены на товары (10–20 товаров)

input_list = [57.8, 46.51, 97, 76.05, 13.11, 87.93, 27, 97.09, 0.16, 42,
        96.64, 34.17, 97.45, 40.62, 84.94, 7, 52.23, 93.74, 89, 3.93]

store_id = id(input_list)
print(input_list)

#5.a
print(f"{'a':-^100}")

end_word:str = ", " # будет ли использованно больше памяти если эта строчка будет в цикле ?

for i, num in enumerate(input_list):

    fix_price = str(f"{float(num):.2f}").split(".")

    if i == len(input_list) - 1:
        end_word = "\n"

    print(f"{fix_price[0]} руб {fix_price[1]} коп", end=end_word)

#5.b
print(f"{'b':-^100}")

print(f"id before sort {store_id}")
input_list.sort()
print(input_list)
print(f"id after sort {id(input_list)}")

if store_id == id(input_list):
    print("In place")
else:
    print("Diff obj")


#5.c
print(f"{'c':-^100}")

copy_of_list = input_list.copy() # or use input_list[:]
copy_of_list.sort(reverse=True) # or use list(sorted()) without copy

print(copy_of_list)
print(store_id)
print(id(copy_of_list))

if store_id == id(copy_of_list):
    print("In place")
else:
    print("Diff obj")



