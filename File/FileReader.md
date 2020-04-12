# FileReader
> FileReader 对象允许Web应用程序异步读取存储在用户计算机上的文件（或原始数据缓冲区）的内容，使用 File 或 Blob 对象指定要读取的文件或数据。

> File对象可以是来自用户在一个```<input>```元素上选择文件后返回的FileList对象,也可以来自拖放操作生成的 DataTransfer对象,还可以是来自在一个HTMLCanvasElement上执行mozGetAsFile()方法后返回结果。

> 重要提示： FileReader仅用于以安全的方式从用户（远程）系统读取文件内容 它不能用于从文件系统中按路径名简单地读取文件。 要在JavaScript中按路径名读取文件，应使用标准Ajax解决方案进行服务器端文件读取，如果读取跨域，则使用CORS权限。

---
## 属性
- FileReader.error 

- FileReader.readyState  
   EMPTY	0	还没有加载任何数据.  
   LOADING	1	数据正在被加载.   
   DONE	2	已完成全部的读取请求.

- FileReader.result  
文件的内容。该属性仅在读取操作完成后才有效，数据的格式取决于使用哪个方法来启动读取操作。
---
## 读取文件方法

- readAsDataURL  
方法会读取指定的 Blob 或 File 对象。读取操作完成的时候，readyState 会变成已完成DONE，并触发 loadend 事件，同时 result 属性将包含一个data:URL格式的字符串（base64编码）以表示所读取文件的内容。
#### 语法
> instanceOfFileReader.readAsDataURL(blob);   
blob: 即将被读取的 Blob 或 File 对象。

- readAsText  
方法可以将 Blob 或者 File 对象转根据特殊的编码格式转化为内容(字符串形式)   
这个方法是异步的，也就是说，只有当执行完成后才能够查看到结果，如果直接查看是无结果的，并返回undefined  
也就是说必须要挂载 实例下的 onload 或 onloadend 的方法处理转化后的结果  
当转化完成后， readyState 这个参数就会转换 为 done 即完成态， event("loadend") 挂载的事件会被触发，并可以通过事件返回的形参得到中的 FileReader.result 属性得到转化后的结果
#### 语法
> instance of FileReader.readAsText(blob[, encoding]);  
二进制对象:Blob类型 或 File类型    
编码类型  (可选):
传入一个字符串类型的编码类型，如缺省，则默认为“utf-8”类型

- readAsArrayBuffer   
接口提供的 readAsArrayBuffer() 方法用于启动读取指定的 Blob 或 File 内容。当读取操作完成时，readyState 变成 DONE（已完成），并触发 loadend 事件，同时 result 属性中将包含一个 ArrayBuffer 对象以表示所读取文件的数据。

#### 语法
> nstanceOfFileReader.readAsArrayBuffer(blob);

- readAsBinaryString  
方法会读取指定的 Blob 或 File 对象，当读取完成的时候，readyState  会变成DONE（已完成），并触发 loadend 事件，同时 result 属性将包含所读取文件原始二进制格式。
#### 语法
> instanceOfFileReader.readAsBinaryString(blob);

- abort  
该方法可以取消 FileReader 的读取操作，触发之后 readyState 为已完成（DONE）
#### 语法
> instanceOfFileReader.abort();

**对readyState为LOADING的fileReader操作**

---
## 事件监听
- FileReader.onloadstart   
=> 处理loadstart事件。该事件在读取操作开始时触发。

- FileReader.onload    
=> 处理load事件。该事件在读取操作完成时触发。

- FileReader.onloadend  
=> 处理loadend事件。该事件在读取操作结束时（要么成功，要么失败）触发。

- FileReader.onerror
=> 处理error事件。该事件在读取操作发生错误时触发。

- FileReader.onabort  
=> 处理abort事件。该事件在读取操作被中断时触发。

- FileReader.onprogress
=> 处理progress事件。该事件在读取Blob时触发。