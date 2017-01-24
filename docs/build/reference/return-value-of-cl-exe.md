---
title: "Valor devuelto de cl.exe | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), valor devuelto"
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Valor devuelto de cl.exe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cl.exe devuelve cero si es correcto \(no tiene errores\) y un valor distinto de cero en caso contrario.  
  
 El valor devuelto de cl.exe puede ser útil si está compilando un script o un archivo de powershell, .cmd o .bat.  Es recomendable que capture el resultado del compilador en caso de que haya errores o advertencias para que pueda resolverlos.  
  
 Hay demasiados códigos de salida de error posibles para que cl.exe los muestre todos.  Puede buscar un código de error en los archivos winerror.h o ntstatus.h incluidos en el Kit de desarrollo de software de Windows, en el directorio %Archivos de programa\(x86\)%\\Windows Kits\\`version`\\Include\\shared\\.  Los códigos de error devueltos en formato decimal deben convertirse en formato hexadecimal para poder realizar la búsqueda.  Por ejemplo, el valor hexadecimal de un código de error \-1073741620 es 0xC00000CC.  Este error se encuentra en ntstatus.h, donde el mensaje correspondiente especificado es: "No se puede encontrar en el servidor remoto el nombre compartido especificado". Para obtener una lista descargable de códigos de error de Windows, vea [&#91;MS\-ERREF&#93;: Windows Error Codes](http://msdn.microsoft.com/es-es/1bc92ddf-b79e-413c-bbaa-99a5281a6c90).  
  
 También puede usar la utilidad de búsqueda de errores de Visual Studio para averiguar lo que significa un mensaje de error del compilador.  En un shell de comandos de Visual Studio, escriba **errlook.exe** para iniciar la utilidad; o en el IDE de Visual Studio, en la barra de menús, elija **Herramientas** y **Búsqueda de errores**.  Escriba el valor del error para buscar texto descriptivo asociado al error.  Para obtener más información, vea [Referencia de ERRLOOK](../../build/reference/errlook-reference.md).  
  
## Comentarios  
 A continuación se muestra un ejemplo de un archivo .bat en el que se utiliza el valor devuelto de cl.exe.  
  
```  
echo off  
cl /W4 t.cpp  
@if ERRORLEVEL == 0 (  
   goto good  
)  
  
@if ERRORLEVEL != 0 (  
   goto bad  
)  
  
:good  
   echo "clean compile"  
   echo %ERRORLEVEL%  
   goto end  
  
:bad  
   echo "error or warning"  
   echo %ERRORLEVEL%  
   goto end  
  
:end  
```  
  
## Vea también  
 [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)