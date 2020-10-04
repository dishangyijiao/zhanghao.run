# Go学习教程
# 本书写作目的、结构以及产出

## 目的
- 教是最好的学习方法，之前学习Ruby的时候，并没完全践行，现在在学习Go要践行起来，写一本教他人入门Go的教程，有效的学习是要有产出的，仅仅学完没有产出，并没有太大的意义，所以在学习Go的过程，需要产出一个Go的开源项目。
## 教程的结构
- Go的发展历史，为什么会出现Go？
- Go有哪些重要的概念？每个概念之间的联系与区别是什么？
- 有哪些优点？
- 有哪些缺点？
- 使用场景有哪些？
- 实现的原理是什么？
- 为什么要这样实现？
- 如果让我自己实现，我会如何实现？（针对存在的问题，进行改进）
- Go的语法 看文档
- 最佳实践都有哪些？
- 有哪些经典的问题没有解决？ 在wiki question中可以回答这个问题
- 未来的发展趋势会怎么样？
- Go的学习资源 Go wiki和awesome完全可以回答这个问题
- 我在Go领域的作品

## 产出

- 写完Go学习教程
- 克隆Ruby一个开源项目

## 如何自学 Go ？

- 原本打算通过两门课程来学习Go，但通读了Go在Github的wiki之后，打算按照wiki的路径学习，其他的付费在线课程作为查漏补缺的。
- 学习的资源
  - Go wiki https://github.com/golang/go/wiki
  - awesome go https://awesome-go.com/
  - Golang https://golang.org/

## 写教程时的想法
- 第一遍是粗略地看，有个全局性地认识，把重要地概念全部整理一遍，对于不懂或者不理解的地方，不要留恋，全部记录下来，在后面的反复学习中逐个解决掉，不能再向之前学习那样，学到一个不懂的地方，必须搞懂再继续往下学，可以先把问题记录下来，在后面学习的过程中解决掉。
- 编程语言最好的学习教材，应当是官方的wiki和非官方的Awesome，其他课程作为补充
- 查看wiki和官方文档的时候，需要将网站中的每一个按钮都点开，看看里面都有什么，不要放过任何一个细节

## 遇到问题如何帮助？
- 使用 golang的help，里面有获得帮助的各种方式，邮件列表、Go论坛、discord等等。https://golang.org/help/
- Go discord，已经加入了，有问题可以再里面提问，加入 10 分钟之后，才可以发送消息
- 加入了 golang-nuts Google group群组 https://groups.google.com/g/golang-nuts
- Gophers slack https://app.slack.com/client/T029RQSE6/D01CJ93LGFJ
- Slack 中的gopher bot非常好用，可以回复关键字，获得相应的帮助
- Go IRC Channel还没搞懂是啥
- 有常见的问题列表，非常不错。https://golang.org/doc/faq 包括Go的各个方面，有疑
- 问的时候，需要在列表中先查找
- HowToAsk https://github.com/golang/go/wiki/HowToAsk
- 关于核心Go开源项目的讨论在golang-dev https://groups.google.com/g/golang-dev

## 如何获取Go的最新消息？
- Go announcement mailing list 邮件公告列表 https://groups.google.com/g/golang-announce
- Go blog https://blog.golang.org/
- Go sub-Reddit https://www.reddit.com/r/golang/
- Go Time Podcast https://changelog.com/gotime
- golangnews https://golangnews.com/
- hashnode https://hashnode.com/n/go
- Matrix enthusiasts https://riot.im/app/#/room/#Go:matrix.org

## 社区资源
- GoUserGroups https://github.com/golang/go/wiki/GoUserGroups
- Golang-China https://groups.google.com/g/golang-china
- Go Playground, A place to write ,run, and share Go code https://play.golang.org/
- Go Wiki https://github.com/golang/go/wiki
- Code of Conduct 参与Go社区的准则和处理issues的报告程序 https://golang.org/conduct
- 开源的Projects https://github.com/golang/go/wiki/Projects

## Go 的插件和集成开发环境
- vscode 安装插件 vscode-go
- Goland Get start https://www.jetbrains.com/go/learn/ 收费的IDE，免费试用 30 天，已经安装了

## 如何发布 Go 的 package
- PackagePublishing https://github.com/golang/go/wiki/PackagePublishing
- 发布Go project 的检查清单 https://github.com/matttproud/gochecklist
- 如何布局Github的 repo https://github.com/golang/go/wiki/GitHubCodeLayout
- 如何让自己的package被发现 https://www.johnsto.co.uk/blog/go-package-go/

## 发现好的课程

- Go(Golang): The Complete Bootcamp https://www.udemy.com/course/learn-go-the-complete-bootcamp-course-golang/
- LearnServerProgramming https://github.com/golang/go/wiki/LearnServerProgramming
- Go CS majors https://github.com/golang/go/wiki/Courses

## Go 的使用者

- 线下开发者交流，可以在meetup网站寻找活动 https://www.meetup.com/find
- 使用Go的公司列表 https://github.com/golang/go/wiki/GoUsers
- 会议列表 https://github.com/golang/go/wiki/Conferences

## 生产环境问题解决

- Goapp性能分析分析 https://blog.golang.org/pprof
- heapdump https://github.com/golang/go/wiki/heapdump
- Go Dashboard https://build.golang.org/perf
- Go Build Coordinator https://farmer.golang.org/builders

# Go的发展历史，为什么会出现Go?

- 发展历史
  -（可以整理一整时间线索图，按照时间线整理每个时间点发生的关键事件，了解整个Go
语言发展的全貌）
  - Go的想法在 2007 年Google内部就已经有了，随着Google规模的逐步发展，整个业务的规模越来越大，开发一个产品的时候，编译的时间越来越长（这个问题的原因需要查资料考证），使整个的开发效率很慢，而C C++在这方面的表现并不好，有各种各样的问题（需要查资料考证，具体的问题是什么，不能笼统的说，不严谨），需要一种更加用生产力的编程语言，在这个大背景下，Go语言就诞生了。2009 的，Go的初始版本发布，最早在Google的哪个项目（需要查资料，具体在哪些项目使用）中应用Go诞生已经有十几年的时间了，现在中国是Go使用非常广泛的地方，很多互联网大厂已经在生产环境使用Go，（需要找出来，国内哪些大厂的哪些项目在使用Go），同时国外的哪些公司也在生产环境使用Go，也需要列举一部分，这是为了说明Go的生态在逐步发展。
- 为什么会出现Go？
  - 从最早的编程语言（需要查资料确认，历史的第一门编程语言，可以追溯到哪里，具体是哪一个）诞生到现在，历史上出现过很多编程语言，有的昙花一现就消失了，有的历久弥新，现在仍然散发着青春的活力，比如C C++ Java，虽然有些编程语言现在不怎么使用了，但他们的设计思想，对后面新的语言产生了很大影响，比如（具体列出几个老语言对后面新语言产生影响的例子）LISP对很多语言都产生了影响。
  - 语言是时代的产物，世界在不断地向前发展，遇到的也是新问题，面对新问题要创造性地去解决，原有的编程语言也能解决，但解决的还不够好，比如在Google，Go产生的背景是规模越来越大，原有的编程语言，在处理大规模的编程 项目时，编译的时间越来越长，效率越来越低，这个时候，需要有一个更有生产力的语言，这是Go诞生的背景。
  - 随着宽带成本的降低（需要验证，这个原因是否正确），使各种服务上云成为了可能，面对大规模、高并发、高可用的需求背景，现有的语言和工具不能解决，Docker、Kubernetes应运而生，而他们都是用Go语言开发的。我认为Go的诞生是一种必然，即使没有Go也会其他Xo的语言，因为有了新的问题，需要创造性的解决。


# Go有哪些重要的概念，以及这些概念之间区别与联系？

## 重要概念

- 原则：
  - 需要整理Go语言中有的，而其他语言中没有的概念，这些部分才需要整理还需要整理虽然Go语言中也有，但是跟常规认识不一样的概念，也需要整理工作区
- GOPATH
- 通道
- 字典
- 指针
- 切片：
- defer语句
- panic函数
- recover函数
- 共享内存并发机制
- CSP并发机制
- 对象池
- package 包
- 在Go中，每一个程序的最上面，都要通过 import ''的方式，引用Go中已有的
- package， 让程序能够运行起来
- sync.pool对象缓存
- sync.Mutex sync.RWMutex
- sync.Cond
- sync.WaitGroup sync.Once
- sync.Pool
- sync.Map
- strings包
- bytes包
- io包
- bufio包
- Pointers
- Allocation
- Concurrency

# 有哪些优点？
# 有哪些缺点？
# 使用场景有哪些？
# 实现的原理是什么？
# 为什么要这样实现？
# 如果让我自己实现，我会如何实现？
- （针对存在的问题，进行改进）
# Go的语法 看文档
# 最佳实践都有哪些？
# 有哪些经典的问题没有解决？
- Go在Github的wiki question中可以回答这个问题
# 未来的发展趋势？
# Go的学习资源
- Go wiki和awesome完全可以回答这个问题
# 我在Go领域的作品
- 教程的完成
- Go领域的开源项目
