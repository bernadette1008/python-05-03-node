# python-05-03-node

파이썬 원형 연결 리스트(node)

```python
#노드 생성
class Node():
    def __init__(self):
        self.data = None
        self.link = None

#노드 추가
def addNode(data):
    global current, head, pre, memory

    current = head
    while current.link != None:
        current = current.link

    node = Node()
    node.data = data
    current.link = node

#노드 삽입
def insertNode(pos, data):
    global current, head, pre, memory

    if head.data == pos:
        node = Node()
        node.data = data
        node.link = head
        head = node
        return

    current = head
    while current.data != pos:
        pre = current
        current = current.link
        if current.data == pos:
            node = Node()
            node.data = data
            node.link = current
            pre.link = node
            return

    node = Node()
    node.data = data
    current.link = node

#노드 삭제
def delNode(pos):
    global current, head, pre, memory

    if head.data == pos:
        current = head
        head = head.link
        del(current)
        return
    
    current = head
    while current != pos:
        pre = current
        current = current.link
        if current.data == pos:
            pre.link = current.link
            del(current)
            return

#노드 출력
def printNode(start):
    current = start
    
    print(current.data, end=" ")

    while current.link != None:
        current = current.link
        print(current.data, end=" ")

# 전역 변수
memory = []
head, current, pre = None, None, None
dataArray = ["다현", "정연", "쯔위", "사나", "지효"]

#node 출력
if __name__ == "__main__" :

    node = Node()
    node.data = dataArray[0]
    head = node
    memory.append(node)

    for data in dataArray[1:] :
        pre = node
        node = Node()
        node.data = data
        pre.link = node
        memory.append(node)

    while 1:
        getnum = int(input("1. 노드 출력 2. 노드 추가 3. 노드 삽입 4. 노드 삭제 0. 종료 : "))

        if getnum == 0:
            break

        elif getnum == 1:
            printNode(head)
            print("\n")
        
        elif getnum == 2:
            data = input("추가할려는 데이터를 입력하시오 : ")
            addNode(data)
        
        elif getnum == 3:
            pos = input("삽입할려는 데이터의 위치(ex: 다현)을 입력하시오. : ")
            data = input("삽입할려는 데이터를 입력하시오 : ")
            insertNode(pos, data)

        elif getnum == 4:
            pos = input("삭제하려는 데이터를 입력하시오. : ")
            delNode(pos)
```
