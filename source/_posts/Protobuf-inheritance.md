title: Protobuf inheritance
date: 2015-08-04 19:21:21
tags:
- protobuf
- all
---

***
1.  protobuf-net for c#
    序列化子类别时,需要在父类中ProtoInclude来确保父类数据，也正确
    别序列化。

        [ProtoInclude(1,typeof(DerivedClass))]
        public class BaseClass
        {
        }
