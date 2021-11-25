import csv


def separateProducts(lst, productList):
    comma = ","
    row = 0
    checkRow = 0
    i = 0
    newRow = 0

    newList = [[0] * 3 for x in range(1000000)]
    newList2 = [[0] * 3 for x in range(1000000)]
    newList[0][0] = "number"
    newList[0][1] = "device_master"
    newList[0][2] = "total_quantity_of_device"

    newList2[0][0] = "number"
    newList2[0][1] = "software_master"
    newList2[0][2] = "typical_product"

    numDevice = lst[0].index('device_master')
    numSoftware = lst[0].index('software_master')
    numTotalQuantity = lst[0].index('total_quantity_of_device')
    numNumber = lst[0].index('number')

    # Deviceのカンマ分け
    # 新しいのリスト（2次元配列で0が入っているもの）を用意し、各要素に代入していく
    # カンマ区切りの処理はさらに別のリスト(boxList)を用意し、そこに区切った後の要素を入れてから新しいリストに入れていく
    # 値が入っていない要素は指定できずIndex Errorが発生するのでそれをキャッチして処理している

    # newRowは加工後のリストの行。rowは元データの行。
    # countはProduct masterと一致する製品名を作成/検出するフラグ。
    # checkNewNumberはデバイス数を一番先頭の製品名に付けるためのフラグ。
    while checkRow != 1:
        checkNewNumber = 0
        try:
            if comma in lst[row + 1][numDevice]:
                boxList = [x.strip() for x in lst[row + 1][numDevice].split(comma)]
                # boxList = lst[row + 1][numDevice].split(comma)
                while i < len(boxList):
                    j = 0
                    count = 0
                    if i == 0:
                        while j < len(productList):
                            if boxList[i] == productList[j][0]:
                                count = 1
                            j = j + 1
                        if count == 1:
                            newList[newRow + 1][0] = lst[row + 1][numNumber]
                            newList[newRow + 1][1] = boxList[i]
                            try:
                                if checkNewNumber == 0:
                                    if lst[row + 1][numTotalQuantity] != "":
                                        newList[newRow + 1][2] = lst[row + 1][numTotalQuantity]
                                    else:
                                        newList[newRow + 1][2] = 0
                                else:
                                    newList[newRow + 1][2] = 0
                            except IndexError:
                                newList[newRow + 1][2] = 0
                            i = i + 1
                            newRow = newRow + 1
                            checkNewNumber = checkNewNumber + 1
                        else:
                            boxList[i + 1] = boxList[i] + ", " + boxList[i + 1]
                            i = i + 1
                    else:
                        while j < len(productList):
                            if boxList[i] == productList[j][0]:
                                count = 1
                            j = j + 1
                        if count == 1:
                            newList[newRow + 1][0] = lst[row + 1][numNumber]
                            newList[newRow + 1][1] = boxList[i]
                            try:
                                if checkNewNumber == 0:
                                    if lst[row + 1][numTotalQuantity] != "":
                                        newList[newRow + 1][2] = lst[row + 1][numTotalQuantity]
                                    else:
                                        newList[newRow + 1][2] = 0
                                else:
                                    newList[newRow + 1][2] = 0
                            except IndexError:
                                newList[newRow + 1][2] = 0
                            i = i + 1
                            newRow = newRow + 1
                            checkNewNumber = checkNewNumber + 1
                        else:
                            boxList[i + 1] = boxList[i] + ", " + boxList[i + 1]
                            i = i + 1
                row = row + 1
                i = 0

            else:
                newList[newRow + 1][0] = lst[row + 1][numNumber]
                newList[newRow + 1][1] = lst[row + 1][numDevice]
                try:
                    if lst[row + 1][numTotalQuantity] != "":
                        newList[newRow + 1][2] = lst[row + 1][numTotalQuantity]
                    else:
                        newList[newRow + 1][2] = 0
                except IndexError:
                    newList[newRow + 1][2] = 0
                row = row + 1
                newRow = newRow + 1

        except IndexError:
            newList[newRow + 1][0] = lst[row + 1][numNumber]
            newList[newRow + 1][1] = ""
            try:
                if lst[row + 1][numTotalQuantity] != "":
                    newList[newRow + 1][2] = lst[row + 1][numTotalQuantity]
                else:
                    newList[newRow + 1][2] = 0
            except IndexError:
                newList[newRow + 1][2] = 0
            row = row + 1
            newRow = newRow + 1

        try:
            if lst[row + 1][numNumber] != 0:
                i = 0
            else:
                checkRow = 1
        except IndexError:
            checkRow = 1

    del newList[newRow + 1:]

    row = 0
    newRow = 0
    checkRow = 0
    i = 0

    # Softwareのカンマ分け
    while checkRow != 1:
        try:
            if comma in lst[row + 1][numSoftware]:
                boxList2 = [y.strip() for y in lst[row + 1][numSoftware].split(comma)]
                while i < len(boxList2):
                    if i == 0:
                        newList2[newRow + 1][0] = lst[row + 1][numNumber]
                        newList2[newRow + 1][1] = boxList2[i]
                        newList2[newRow + 1][2] = True
                        i = i + 1
                        newRow = newRow + 1
                    else:
                        newList2[newRow + 1][0] = lst[row + 1][numNumber]
                        newList2[newRow + 1][1] = boxList2[i]
                        newList2[newRow + 1][2] = False
                        i = i + 1
                        newRow = newRow + 1

                row = row + 1
                i = 0

            else:
                newList2[newRow + 1][0] = lst[row + 1][numNumber]
                newList2[newRow + 1][1] = lst[row + 1][numSoftware]
                newList2[newRow + 1][2] = True
                row = row + 1
                newRow = newRow + 1

        except IndexError:
            newList2[newRow + 1][0] = lst[row + 1][numNumber]
            newList2[newRow + 1][1] = ""
            newList2[newRow + 1][2] = True
            row = row + 1
            newRow = newRow + 1

        try:
            if lst[row + 1][numNumber] != 0:
                i = 0
            else:
                checkRow = 1
        except IndexError:
            checkRow = 1

    del newList2[newRow + 1:]

    with open('C:/PythonProject/カンマ区切り/separate_device.csv', 'w', encoding='utf-8_sig', newline="") as fs:
        i = 0
        while i < len(newList):
            writer = csv.writer(fs)
            writer.writerow(newList[i])
            i = i + 1

    with open('C:/PythonProject/カンマ区切り/separate_software.csv', 'w', encoding='utf-8_sig', newline="") as fa:
        i = 0
        while i < len(newList2):
            writer = csv.writer(fa)
            writer.writerow(newList2[i])
            i = i + 1

    fs.close()
    fa.close()


with open('C:/PythonProject/カンマ区切り/x_rcls_customize_deal.csv', 'r') as fp:
    lst = list(csv.reader(fp))
    with open('C:/PythonProject/カンマ区切り/u_product_master.csv', 'r') as fx:
        productList = list(csv.reader(fx))
        separateProducts(lst, productList)

fp.close()
fx.close()
