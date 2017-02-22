---
title: "XDCMake (Referencia) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xdcmake"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "xdcmake (programa)"
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# XDCMake (Referencia)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

xdcmake.exe es un programa que los archivos de compilaciones válida en un archivo .xml.  Un archivo .xdc es creado por el compilador de Visual C\+\+ para cada archivo de código fuente cuando el código fuente se compila con [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) y cuando el archivo de código fuente contiene los comentarios de documentación marcados para buscar con etiquetas XML.  
  
### Para utilizar xdcmake.exe en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md).  
  
2.  Abra la carpeta **Propiedades de configuración** .  
  
3.  Haga clic en la página de propiedades **Los comentarios del documento XML**.  
  
> [!NOTE]
>  las opciones de xdcmake.exe en la línea de comandos difieren de las opciones cuando xdcmake.exe se utiliza en el entorno de desarrollo \(páginas de propiedades\).  Para obtener información sobre cómo utilizar xdcmake.exe en el entorno de desarrollo, vea [Herramienta Generador de documentos XML \(Páginas de propiedades\)](../ide/xml-document-generator-tool-property-pages.md).  
  
## Sintaxis  
 xdcmake `input_filename options`  
  
## Parámetros  
 donde:  
  
 `input_filename`  
 El nombre de archivo de los archivos .xdc utilizados como entrada a xdcmake.exe.  Especifica uno o más archivos .xdc o utilice \*.xdc para utilizar todos los archivos .xdc en el directorio actual.  
  
 `options`  
 Cero o más de los siguientes:  
  
|Opción|Descripción|  
|------------|-----------------|  
|\/? , \/help|Mostrar ayuda para xdcmake.exe.|  
|\/assembly:*nombre de archivo*|Permite especificar el valor de la etiqueta de \<assembly\> en el archivo .xml.  De forma predeterminada, el valor de la etiqueta de \<assembly\> es igual que el nombre del archivo .xml.|  
|\/nologo|Suprime el mensaje de copyright.|  
|\/out:*nombre de archivo*|Permite especificar el nombre del archivo .xml.  De forma predeterminada, el nombre del archivo .xml es el nombre del primer archivo .xdc procesado por xdcmake.exe.|  
  
## Comentarios  
 Visual Studio llamará a xdcmake.exe automáticamente al compilar un proyecto.  También puede invocar xdcmake.exe en la línea de comandos.  
  
 Vea [Etiquetas recomendadas para comentarios de documentación](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) para más información en los comentarios de documentación a los archivos de código fuente.  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)