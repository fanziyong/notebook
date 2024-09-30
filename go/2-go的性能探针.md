####
````text
以往针对黑盒程序，我们只能用监控和事前事后的对比来获取具体的性能数据，当我们具备对程序的定制能力的时候，就可以直接用 profiler 程序来进行程序运行过程中的性能指标采集了。
借助 pprof 的能力，我们可以快速的在上面代码的 Web 服务中添加几个和性能相关的接口。多数文章会告诉你引用 pprof 这个模块就可以了，其实不然。因为阅读代码（https://cs.opensource.google/go/go/+/refs/tags/go1.17.6:src/net/http/pprof/pprof.go），我们可知，pprof 的“性能监控接口自动注册”的能力，仅针对默认的 http 服务有效，而不会针对多路复用（mux）的 http 服务生效：
````

````go
func init() {
	http.HandleFunc("/debug/pprof/", Index)
	http.HandleFunc("/debug/pprof/cmdline", Cmdline)
	http.HandleFunc("/debug/pprof/profile", Profile)
	http.HandleFunc("/debug/pprof/symbol", Symbol)
	http.HandleFunc("/debug/pprof/trace", Trace)
}
````