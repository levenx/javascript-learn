### Blob
> Blob 对象表示一个不可变、原始数据的类文件对象。Blob 表示的不一定是JavaScript原生格式的数据。File 接口基于Blob，继承了 blob 的功能并将其扩展使其支持用户系统上的文件。  
要从其他非blob对象和数据构造一个 Blob，请使用 Blob() 构造函数。要创建一个 blob 数据的子集 blob，请使用 slice() 方法。

- 构造方法  
Blob(blobParts[, options])

---
### 属性
- Blob.size   
Blob 对象中所包含数据的大小（字节）

- Blob.type   
一个字符串，表明该 Blob 对象所包含数据的 MIME 类型。如果类型未知，则该值为空字符串。

--- 
### 方法
- Blob.slice([start[, end[, contentType]]])   
返回一个新的 Blob 对象，包含了源 Blob 对象中指定范围内的数据。

- Blob.stream()  
返回一个能读取blob内容的 ReadableStream。

- Blob.text()  
返回一个promise且包含blob所有内容的UTF-8格式的 USVString。

- Blob.arrayBuffer()   
返回一个promise且包含blob所有内容的二进制格式的 ArrayBuffer 

---
# File

构造方法
> var myFile = new File(bits, name[, options]);  
bits :一个包含ArrayBuffer，ArrayBufferView，Blob，或者 DOMString 对象的 Array — 或者任何这些对象的组合。这是 UTF-8 编码的文件内容。  
name:USVString，表示文件名称，或者文件路径。  
options 可选
选项对象，包含文件的可选属性。可用的选项如下：  
type: DOMString，表示将要放到文件中的内容的 MIME 类型。默认值为 "" 。  
lastModified: 数值，表示文件最后修改时间的 Unix 时间戳（毫秒）。默认值为 Date.now()。

### 属性
- File.lastModified 
- File.name
- File.size 
- File.type
> 媒体类型（通常称为 Multipurpose Internet Mail Extensions 或 MIME 类型 ）是一种标准，用来表示文档、文件或字节流的性质和格式。    
> text/plain   
text/html   
image/jpeg   
image/png   
audio/mpeg   
audio/ogg   
audio/*   
video/mp4   
application/*   
application/json   
application/javascript   
application/ecmascript   
application/octet-stream  


[MIME](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Basics_of_HTTP/MIME_types)