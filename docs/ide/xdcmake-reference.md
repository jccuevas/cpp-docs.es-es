---
title: XDCMake (referencia) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xdcmake
dev_langs: C++
helpviewer_keywords: xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea635d701b4dea2471067072083d9568f11f3d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="xdcmake-reference"></a>XDCMake (Referencia)
xdcmake.exe es un programa que se compila el archivo .xdc en un archivo .xml. Se crea un archivo .xdc por el compilador de Visual C++ para cada archivo de código fuente cuando se compila código fuente con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) y cuando el archivo de código fuente contiene comentarios de documentación marcados con etiquetas XML.  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Para usar xdcmake.exe en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
2.  Abra la **propiedades de configuración** carpeta.  
  
3.  Haga clic en el **comentarios de documentos XML** página de propiedades.  
  
> [!NOTE]
>  Opciones de XDCMake.exe en la línea de comandos difieren de las opciones cuando se utiliza xdcmake.exe en el entorno de desarrollo (páginas de propiedades). Para obtener información sobre cómo utilizar xdcmake.exe en el entorno de desarrollo, consulte [XML Document Generator Tool Property Pages](../ide/xml-document-generator-tool-property-pages.md).  
  
## <a name="syntax"></a>Sintaxis  
 XDCMake`input_filename options`  
  
## <a name="parameters"></a>Parámetros  
 donde:  
  
 `input_filename`  
 El nombre de archivo de los archivos .xdc utilizados como entrada para xdcmake.exe. Especifique uno o más archivos .xdc o use *.xdc para utilizar todos los archivos .xdc en el directorio actual.  
  
 `options`  
 Cero o más de las siguientes acciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|/?, / help|Mostrar la Ayuda de xdcmake.exe.|  
|/Assembly:*nombre de archivo*|Le permite especificar el valor de la \<ensamblado > etiqueta en el archivo .xml.  De forma predeterminada, el valor de la \<ensamblado > etiqueta es el mismo que el nombre de archivo del archivo. Xml.|  
|/nologo|Suprimir mensaje de copyright.|  
|/ out:*nombre de archivo*|Permite especificar el nombre del archivo. Xml.  De forma predeterminada, el nombre del archivo .xml es el nombre de archivo del primer archivo .xdc procesado por xdcmake.exe.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio llamará xdcmake.exe automáticamente al crear un proyecto. También puede invocar xdcmake.exe en la línea de comandos.  
  
 Vea [etiquetas recomendadas para comentarios de documentación](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) para obtener más información sobre cómo agregar comentarios de documentación a archivos de código fuente.  
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)