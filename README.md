import jason
import datetime
import os
data_file = "tasks.json"
def load_tasks():
  if os.path.exists(data_file):
  with open(data_file,"r") as f:
  return json.load(f)
  return[]
def save(tasks):
    with open(data_file,"w") as f:
    json.dump(tasks,f,indent=4)
tasks=load_tasks()
def add_task():
    task_name=input("task:").strip()
    deadline=input("deadline(YYYY-MM-DD) or leave blank:").strip()
    task={
        "name": task_name
        "done": False,
        "deadline": deadline if deadline
else None,
         "completed_on":None
     }
     tasks.append(task)
     save(task)
     print("added.")
def show_tasks():
    print("\n--- Your tAKA ---")
    if not tasks:
       print("no tasks yet.")
       return
    for idx, t in enumerate(tasks,start=1):
        mark="done" if t["done"] else "not done"
        line=f"{idx}. {t['name']} [{mark}]"
        if t["deadline"]:
           line += f"(deadline:{t['deadline']})"
           print(line)
        print("------------\n")
def finish_task():
    show_tasks()
    if not tasks:
       return
    try:
        num=int(input("which task number is done"))
        if num<1 or num>len(tasks):
           print("invalid.")
           return
    except:
        print("enter the number")
        return
    tasks[num - 1]["done"] = true
    tasks[num - 1]["completed_on"] =str(datetime.date.today())
    save(tasks)
    done_today=sum(
        1 for t in tasks
        if t["done"] and 
    t["completed_on"==str(date.time.date.today())
    )
    if done_today == 1:
      print("nice! first fask of day done")
    elif done_today ==3:
      print("wow,3 tasks today!keep going")
    elif done_today >=5:
      print("productivity beast mode on")
  def deadline_warnings():
      today = datetime.date.today()
      for t in tasks:
          if not t["deadline"] or t["done"]:
              continue
          try:
              d=datetime.datetime.strptime(t["deadline"] , "%Y-%M-%d").date()
          except:
               continue
          days=(d-today).days
          if days <0:
             print(f"!'{t['name']}' is overdue!")
          elif days <=2:
              print("deadline coming:'{t['name']}' ({days} days left)")
def focus_mode():
      print("\nentering focus mode...\n")
      pending = [t for in tasks if not 
  t["done"]]
      if not pending:
         print("everything is done. free mind")
         return
      for t in pending:
          print("next task:")
          print("-", t["name"])
          input("press enter for the next task..")
          print("focus session over.\n")
def main() :
    while true:
        print("1. add task")
        print("2. view task")
        print("3. mark task done")
        print("4. focus mode")
        print("5. exit")
        deadline_warnings()
        choice= input("choose:").strip()
        if choice == "1":
            add_task()
        elif choice == "2":
            show_task()
        elif choice=="3":
            finish_task()
        elif choice=="4":
            focus_mode()
        elif choice=="5":
             break
        else:
            print("pick a number 1-5 .\n")
main()           
    
    

        

