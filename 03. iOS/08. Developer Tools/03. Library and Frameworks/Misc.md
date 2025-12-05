[toc]

##### Static lib (.a) vs Dynamic framework (.framework) composition

Libraries are collections of object files in an archive created by the program `ar`, indexed by a program `ranlib`.

All libraries link object files.

![image-20251206113110977](./assets/image-20251206113110977.png)

##### Dynamic library vs Dynamic framework

![image-20251206132549322](./assets/image-20251206132549322.png)

##### xcFramework composition

![image-20251206112930890](./assets/image-20251206112930890.png)

> Incremental builds in Xcode do reuse object files though

