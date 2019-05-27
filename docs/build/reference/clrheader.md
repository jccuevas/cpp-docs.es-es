---
title: /CLRHEADER
ms.date: 05/16/2019
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 5974606448dad103c8f12a126b8d17c688927c88
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837162"
---
# <a name="clrheader"></a>/CLRHEADER

Muestra información específica del CLR.

## <a name="syntax"></a>Sintaxis

> /CLRHEADER *file*

### <a name="arguments"></a>Argumentos

*file*<br/>
Archivo de imagen creado con [/clr](clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Comentarios

**/CLRHEADER** muestra información sobre los encabezados de .NET usados en un programa administrado. El resultado muestra la ubicación y el tamaño, en bytes, del encabezado de .NET y las secciones en el encabezado.

En los archivos producidos con la opción del compilador [/GL](gl-whole-program-optimization.md), solo está disponible la opción [/HEADERS DUMPBIN](headers.md).

Cuando **/CLRHEADER** se usa en un archivo que se compiló con /clr, habrá una sección **clr Header:** en el resultado de dumpbin. El valor de **flags** indica qué opción de /clr se usó:

- 0 -- /clr (la imagen puede contener código nativo).

También se puede comprobar mediante programación si una imagen se generó para Common Language Runtime.  Para obtener más información, vea [Cómo: Determinar si una imagen es nativa o CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

Las opciones del compilador **/clr:pure** y **/clr:safe** han quedado en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017 y versiones posteriores. El código que tenga que ser "puro" o "seguro" deberá portarse a C#.

## <a name="see-also"></a>Vea también

- [Opciones de DUMPBIN](dumpbin-options.md)
