class Student:
    def __init__(self, name, chinese,math,english):
        self.name = name
        self.chinese=chinese
        self.math=math
        self.english=english
    def __str__(self):
        return f"姓名:{self.name}|语文:{self.chinese}|数学:{self.math}|英语:{self.english}|总分:{self.chinese+self.english+self.math}"
class StudentSystem:
    def __init__(self):
        self.students = []
    def add_student(self):
        name=input("请输入学生姓名:")
        for i in self.students:
            if i.name == name:
                print("已添加,请重新选择")
                return
        new_chinese=int(input("请输入语文成绩:"))
        new_math =int(input("请输入数学成绩:"))
        new_english =int(input("请输入英语成绩:"))
        if 0 <= new_chinese <= 100 and 0 <= new_math <= 100 and 0 <= new_english <= 100:
            s1 = Student(name, new_chinese, new_math, new_english)
            self.students.append(s1)
            print("添加完成")
            return
        else:
            print("数字错误")
    def modify_student(self):
        name = input("请输入学生姓名:")
        for i in self.students:
            if i.name == name:
                print(f"当前成绩:{i}")
                new_chinese = int(input("请输入语文成绩:"))
                new_math = int(input("请输入数学成绩:"))
                new_english = int(input("请输入英语成绩:"))
                if 0<=new_chinese<=100 and 0<=new_math<=100 and 0<=new_english<=100:
                    i.chinese=new_chinese
                    i.math=new_math
                    i.english=new_english
                    print(f"现在成绩:{i}")
                    print("修改成功")
                    return
                else:
                    print("数字错误")
        print("未找到该学生")
    def delete_student(self):
        name = input("请输入学生姓名:")
        for i in self.students:
            if i.name == name:
                self.students.remove(i)
                print("删除成功")
                return
        print("未找到该学生")
    def check_student(self):
        name = input("请输入学生姓名:")
        for i in self.students:
            if i.name == name:
                print(f"{i}")
                return
        print("未找到该学生")
    def list_student(self):
        for i in self.students:
            print(f"{i}")
    def run(self):
        while True:
            print(
                "# # # # # # # # # # # # # # # # # # # # # # # # # # [菜单]# # # # # # # # # # # # # ## # # # # # # # # # # # # #\n"
                "#                    1.添加学生信息  2.修改学生信息  3.删除学生信息  4.查询学生信息  5.列出所有学生   6.退出系统            #\n"
                "# # # # # # # # # # # # # # # # # # # # # # # # # # [菜单]# # # # # # # # # # # # # ## # # # # # # # # # # # # #\n ")
            print()
            choice = input("请输入编号(1-6):")
            try:
                match choice:
                    case "1":
                        self.add_student()
                    case "2":
                        self.modify_student()
                    case "3":
                        self.delete_student()
                    case "4":
                        self.check_student()
                    case "5":
                        self.list_student()
                    case "6":
                        print("bye,bye")
                        break
                    case _:
                        print("操作有误")
            except Exception as e:
                print("输入的数据有问题，请重新输入",e)
if __name__ == "__main__":
    s = StudentSystem()
    s.run()








