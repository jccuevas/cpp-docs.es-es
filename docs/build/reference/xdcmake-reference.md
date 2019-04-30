---
title: XDCMake (Referencia)
ms.date: 11/04/2016
f1_keywords:
- xdcmake
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
ms.openlocfilehash: 097c105e005a3c734ba86139ed3b4b6ecdcf49d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316397"
---
# <a name="xdcmake-reference"></a>XDCMake (Referencia)

xdcmake.exe es un programa que compila los archivos .xdc en un archivo .xml. Se crea un archivo .xdc por el compilador MSVC para cada archivo de código fuente cuando se compila código fuente con [/doc](doc-process-documentation-comments-c-cpp.md) y cuando el archivo de código fuente contiene comentarios de documentación que se ha marcado con etiquetas XML.

### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Para usar xdcmake.exe en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Abra la carpeta **Propiedades de configuración**.

1. Haga clic en la página de propiedades **Comentarios de documentos XML**.

> [!NOTE]
>  Las opciones de xdcmake.exe en la línea de comandos difieren de las opciones cuando se usa en el entorno de desarrollo (las páginas de propiedades). Para obtener información sobre cómo usar xdcmake.exe en el entorno de desarrollo, vea [Herramienta Generador de documentos XML (Páginas de propiedades)](xml-document-generator-tool-property-pages.md).

## <a name="syntax"></a>Sintaxis

xdcmake `input_filename options`

## <a name="parameters"></a>Parámetros

*input_filename*<br/>
El nombre de archivo de los archivos .xdc que se usan como entrada para xdcmake.exe. Especifique uno o más archivos .xdc, o bien use *.xdc para utilizar todos los archivos .xdc en el directorio actual.

*options*<br/>
Cero o más de las opciones siguientes:

|Opción|Descripción|
|------------|-----------------|
|/?, /help|Muestra la ayuda de xdcmake.exe.|
|/assembly:*nombre_de_archivo*|Permite especificar el valor de la etiqueta \<assembly> en el archivo .xml.  De forma predeterminada, el valor de la etiqueta \<assembly> es el mismo que el nombre de archivo del archivo .xml.|
|/nologo|Se suprime el mensaje de copyright.|
|/out:*nombre_de_archivo*|Permite especificar el nombre del archivo .xml.  De forma predeterminada, el nombre del archivo .xml es el nombre del primer archivo .xdc procesado por xdcmake.exe.|

## <a name="remarks"></a>Comentarios

Visual Studio llamará a xdcmake.exe de manera automática al compilar un proyecto. xdcmake.exe también se puede invocar desde la línea de comandos.

Vea [Etiquetas recomendadas para los comentarios de documentación](recommended-tags-for-documentation-comments-visual-cpp.md) para obtener más información sobre cómo agregar comentarios de documentación a los archivos de código fuente.

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)
