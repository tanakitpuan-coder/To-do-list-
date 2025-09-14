todo_list = []

while True:
    command = input("กรุณาใส่คำสั่ง (add, list, remove, exit): ").strip()
    if command.lower().startswith("add "):
        task = command[4:].strip()
        if task:
            todo_list.append(task)
            print(f'เพิ่ม "{task}" ในรายการแล้ว')
        else:
            print("กรุณาระบุงานที่ต้องการเพิ่ม")
    elif command.lower() == "list":
        if not todo_list:
            print("ยังไม่มีงานในรายการ")
        else:
            for idx, task in enumerate(todo_list, 1):
                print(f"{idx}. {task}")
    elif command.lower().startswith("remove "):
        try:
            num = int(command[7:].strip())
            if 1 <= num <= len(todo_list):
                removed = todo_list.pop(num - 1)
                print(f'ลบ "{removed}" ออกจากรายการแล้ว')
            else:
                print("หมายเลขงานไม่ถูกต้อง")
        except ValueError:
            print("กรุณาระบุหมายเลขงานที่ต้องการลบ")
    elif command.lower() == "exit":
        print("ออกจากโปรแกรม")
        break
    else:
        print("ไม่รู้จักคำสั่งนี้")

