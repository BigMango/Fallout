代码产生断点

```python
# 5678 is the default attach port in the VS Code debug configurations. Unless a host and port are specified, host defaults to 127.0.0.1
debugpy.listen(5678)
print("Waiting for debugger attach")
debugpy.wait_for_client()
debugpy.breakpoint()
print('break on this line')
```


// todo0 toml 项目配置


[How to use C# Class Libraries (dll) in Python](https://discourse.mcneel.com/t/how-to-use-c-class-libraries-dll-in-python/164168/19)