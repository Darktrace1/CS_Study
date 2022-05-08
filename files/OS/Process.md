# Process

## 1. 프로세스(Process)

> 프로세스는 메인 메모리에 할당되어 실행중인 프로그램을 의미한다. 프로그램은 Disk에 저장되어 현재 아무 일도 하지않는 수동적인 상태이다. 프로세스는 실행하면서 stack, heap, data 등이 끊임없이 변한다.

### 1.1 프로세스 상태(Process State)
<p align="center">
    <img src = "../../Pictures/OS_1.png">
</p>

> Diagram of Process State, 프로세스 상태 다이어그램은 new 상태에서부터 terminated 상태까지 프로세스가 거치는 상태가 어떤 작업에 의해 변하는지를 나타낸 그림

<ul> 
  <li><b>New</b>: 프로세스가 새롭게 생성</li>
  <li><b>Running</b>: 프로세서가 해당 프로세스를 실행 중인 상태</li>
  <li><b>Waiting</b>: Running 상태 중 I/O 요청이 들오면 해당 프로세스를 Waiting Queue로 보내고 I/O 요청이 종료될때까지 대기시킨다. 이때 프로세서가 비어있기에 스케줄러가 다른 process를 실행</li>
  <li><b>Ready</b>: 할당된 프로세스가 실행을 위한 모든 준비를 마치고 기다리는 상태</li>
  <li><b>Terminated</b>: 프로세스가 완전히 종료된 상태</li>
</ul>

### 1.2 PCB(Process Control Block)
<p align="center">
    <img src = "../../Pictures\OS_2.png">
</p>

> PCB는 프로세스에 대한 모든 정보를 저장하는 자료구조로, Task Control Block(TCB)으로 불리기도 한다. 
> PCB는 프로세스 상태, Program Counter(PC), CPU 레지스터, CPU 스케줄링 정보, Accounting Information(CPU 점유율 등) 등 프로세스가 가지는 정보의 대부분을 저장하고 있다.
> 프로세스는 하나의 프로세스가 모든 작업을 완료할때까지 동작하지 않고 끊임없이 구동 프로세스를 변경하며 수행한다. 이때 프로세스의 변경이 일어날때 기존에 처리중인 프로세스의 정보를 저장하고 있어야 다음에
> 이어서 작업을 수행할 수 있는데 이때 사용되는 것이 PCB인 것이다.

### 1.3 Process Scheduling
> CPU 사용을 극대화 하기 위해서는 프로세스의 전환이 빨라야 하는데, 이때 어떤 프로세스를 고를지에 대한 기준이 필요하다. 이 기준, 즉 순서를 정해주는 알고리즘을 스케줄링(Scheduling)이라고 한다.
> 그리고 각 프로세스가 본인의 순서가 올때까지 대기하는 장소를 큐(Queue)라고 한다.

큐는 상황에 맞는 여러 큐가 필요한데 대표적인 큐는 다음과 같다.
<ul>
  <li><b>Job Queue(Job Scheduler, Long-term Scheduler)</b> - Disk에 있는 프로그램이 실행되기 위해 메인 메모리의 할당 순서를 기다리는 큐</li>
  <li><b>Ready Queue(CPU Scheduler, Short-term Scheduler)</b> - CPU에서의 구동을 기다리는 큐, 메인 메모리에 있고 실행가능한 상태를 표현</li>
  <li><b>Device Queue(Device Scheduler)</b> - I/O Device가 잠깐 대기하는 큐</li>
</ul>

스케줄러는 크게 2가지로 나뉜다.
<ul>
  <li><b>Short-term Scheduler(CPU Scheduler)</b> - 어떤 프로세스를 CPU에 올릴 것인지에 대해 결정하는 스케줄러로 스케줄링이 발생하는 시간이 매우 짧다는 특징이 있다</li>
  <li><b>Long-term Scheduler(Job Scheduler)</b> - 어떤 프로세스(Job)를 구동할 것인가(어떤 프로세스를 Ready Queue에 넣을 것인가?)를 결정하는 스케줄러로 비교적 오래걸린다는 특징이 있다</li>
</ul>

### 1.4 Context Switch(문맥 전환)
Context switching은 CPU가 한 프로세스에서 다른 프로세스로 옮겨가는 것을 말한다. 즉, 한 프로세스가 실행중인 것을 멈추고 다른 프로세스가 실행되는 것이다.

<ul>
  <li><b>Scheduler</b> - CPU Scheduler를 말하며, CPU가 어느 프로세스를 선택할지 정한다.</li>
  <li><b>Dispatcher</b> - 실제 context switching이 발생하면 CPU의 내부 데이터를 이전 프로세스 데이터에서 새로 시작되는 데이터로 바꿔준다. 다시 말해서 현재 CPU 데이터는 이전 프로세스의 PCB에 갱신하고, 새로 시작되는 프로세스의 PCB 데이터를 CPU로 Restore 해준다.</li>
  <li><b>Context switching overhead</b> - Context switching이 발생할 때마다, dispatcher에서 수행하는 작업을 매번 수행해야하며 이 모든 것은 overhead이다. 그리고 문맥 전환은 매우 자주 발생하는 작업이므로 overhead를 줄이기 위해서는 dispatcher를 구현하는 코드에 대한 효율을 최대한 높여주어야한다.</li>
</ul>
