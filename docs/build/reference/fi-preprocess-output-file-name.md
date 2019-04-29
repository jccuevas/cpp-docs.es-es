---
title: /Fi (Preprocesar el nombre del archivo de salida)
ms.date: 11/04/2016
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 990c48a72c3f6017d893ddf9b46bcbb737bfb634
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271260"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (Preprocesar el nombre del archivo de salida)

Especifica el nombre del archivo de salida a la que el [/P (Preprocesar para un archivo)](p-preprocess-to-a-file.md) opción del compilador escribe la salida preprocesada.

## <a name="syntax"></a>Sintaxis

```
/Fipathname
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`pathname`|El nombre y ruta de acceso del archivo de salida generados por el **/P** opción del compilador.|

## <a name="remarks"></a>Comentarios

Use la **/Fi** en combinación con la opción del compilador la **/P** opción del compilador.

Si especifica solo una ruta de acceso para el `pathname` parámetro, el nombre base del archivo de origen se utiliza como nombre base del archivo de salida preprocesado. El `pathname` parámetro no requiere una extensión de nombre de archivo determinado. Sin embargo, una extensión de "i" se usa si no especifica una extensión de nombre de archivo.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos preprocesa PROGRAM.cpp, conserva los comentarios, agrega [#line](../../preprocessor/hash-line-directive-c-cpp.md) directivas y escribe el resultado en el archivo MYPROCESS.i.

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[/P (Preprocesar para archivo)](p-preprocess-to-a-file.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
