---
title: -Fe (nombre al archivo EXE) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /fe
dev_langs: C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 83965ef2bf64f77dbcb1eb9832e7178c30260d16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fe-name-exe-file"></a>/Fe (Asignar nombre a un archivo ejecutable)
Especifica un nombre y un directorio para el archivo .exe o el archivo DLL creado por el compilador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Fepathname  
```  
  
## <a name="remarks"></a>Comentarios  
 Sin esta opción, el compilador asigna al archivo un nombre predeterminado con el nombre base del primer archivo origen o el objeto especificado en la línea de comandos y la extensión .exe o .dll.  
  
 Si especifica la[/c (compilar sin vincular)](../../build/reference/c-compile-without-linking.md), para compilar sin vinculación, **/Fe** no tiene ningún efecto.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **General**página de propiedades.  
  
4.  Modificar el **archivo de salida** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.  
  
## <a name="example"></a>Ejemplo  
 La línea de comandos siguiente compila y vincula todos los archivos de origen de C en el directorio actual. El archivo ejecutable resultante se denomina PROCESS.exe y se crea en el directorio C:\BIN.  
  
```  
CL /FeC:\BIN\PROCESS *.C  
```  
  
## <a name="example"></a>Ejemplo  
 La siguiente línea de comandos crea un archivo ejecutable en `C:\BIN` con el mismo nombre base que el primer archivo de origen o de objeto:  
  
```  
CL /FeC:\BIN\ *.C  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)