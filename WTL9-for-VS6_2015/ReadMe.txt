# WTL
下载官方源：http://wtl.sourceforge.net/
官方支持版本：Visual Studio 2013 及以下版本
===================================
Visual Studio 2015版本的需要如下操作
一定要下载该GIT下的修复过的压缩包，官方源用于有兴趣者对比修改内容

# Visual Studio 2015 安装步骤：
1.解压WTL91_5321_FINAL.ZIP
===================================
2.复制Include下的所有头文件拷贝到%VS2015_INSTALLDIR%\VC\Include目录下
===================================
3.在%VS2015_INSTALLDIR%\VC\VCWizards\AppWiz目录下新建WTL目录，
===================================
  复制解压后的AppWiz目录到WTL目录中
===================================
4.双击执行Setup.js,提示均同意，完成安装！ 
===================================
5.OK！可以新建WTL工程一步一步开心玩耍了！
===================================

如还是遇到错误，则尝试一下方法：
AppType.htm的第443到451行、default.htm的第509到517行、UIFeatures.htm的第516到524行：

          < SCRIPT > 
     var  strPath  =  window.external.FindSymbol( " PRODUCT_INSTALLATION_DIR " );
    strPath  +=   " VCWizards/ " ;
    strPath  +=  window.external.GetHostLocale();
     var  strScriptPath  =  strPath  +   " /Script.js " ;
     var  strCommonPath  =  strPath  +   " /Common.js " ;
    document.scripts( " INCLUDE_SCRIPT " ).src  =  strScriptPath;
    document.scripts( " INCLUDE_COMMON " ).src  =  strCommonPath;
         </ SCRIPT > 
      需要修改为：
        <SCRIPT>
    document.scripts("INCLUDE_SCRIPT").src = window.external.FindSymbol("SCRIPT_COMMON_PATH") + "/Script.js";
    document.scripts("INCLUDE_COMMON").src = window.external.FindSymbol("SCRIPT_COMMON_PATH") + "/Common.js";
        </SCRIPT>
     
      原因是Script.js与Common.js两个文件的路径指向错误，因此无法读取这两个文件中的所定义的函数。
      
#作者：xingyun86
#QQ：523381005
#邮箱:xingyun_ppshuai@yeah.net
