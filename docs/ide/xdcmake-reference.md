---
title: XDCMake (Referencia) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- xdcmake
dev_langs:
- C++
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 383347dc5cd1ce0dcadff6bdee802b90fd52e85d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33333910"
---
# <a name="xdcmake-reference"></a>XDCMake (Referencia)
xdcmake.exe es un programa que compila los archivos .xdc en un archivo .xml. El compilador de Visual C++ crea un archivo .xdc para cada archivo de código fuente cuando el código fuente se compila con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) y cuando el archivo de código fuente contiene comentarios de documentación marcados con etiquetas XML.  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Para usar xdcmake.exe en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../ide/working-with-project-properties.md).  
  
2.  Abra la carpeta **Propiedades de configuración**.  
  
3.  Haga clic en la página de propiedades **Comentarios de documentos XML**.  
  
> [!NOTE]
>  Las opciones de xdcmake.exe en la línea de comandos difieren de las opciones cuando se usa en el entorno de desarrollo (las páginas de propiedades). Para obtener información sobre cómo usar xdcmake.exe en el entorno de desarrollo, vea [Herramienta Generador de documentos XML (Páginas de propiedades)](../ide/xml-document-generator-tool-property-pages.md).  
  
## <a name="syntax"></a>Sintaxis  
 xdcmake `input_filename options`  
  
## <a name="parameters"></a>Parámetros  
 donde:  
  
 `input_filename`  
 El nombre de archivo de los archivos .xdc que se usan como entrada para xdcmake.exe. Especifique uno o más archivos .xdc, o bien use *.xdc para utilizar todos los archivos .xdc en el directorio actual.  
  
 `options`  
 Cero o más de las opciones siguientes:  
  
|Opción|Description|  
|------------|-----------------|  
|/?, /help|Muestra la ayuda de xdcmake.exe.|  
|/assembly:*nombre_de_archivo*|Permite especificar el valor de la etiqueta \<assembly> en el archivo .xml.  De forma predeterminada, el valor de la etiqueta \<assembly> es el mismo que el nombre de archivo del archivo .xml.|  
|/nologo|Se suprime el mensaje de copyright.|  
|/out:*nombre_de_archivo*|Permite especificar el nombre del archivo .xml.  De forma predeterminada, el nombre del archivo .xml es el nombre del primer archivo .xdc procesado por xdcmake.exe.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio llamará a xdcmake.exe de manera automática al compilar un proyecto. xdcmake.exe también se puede invocar desde la línea de comandos.  
  
 Vea [Etiquetas recomendadas para los comentarios de documentación](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) para obtener más información sobre cómo agregar comentarios de documentación a los archivos de código fuente.  
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)