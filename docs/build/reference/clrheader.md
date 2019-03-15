---
title: /CLRHEADER
ms.date: 11/04/2016
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 6a1240e2d3ad2ac3a454c610a6f49d07e50951e5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820707"
---
# <a name="clrheader"></a>/CLRHEADER

Mostrar información específica de CLR.

## <a name="syntax"></a>Sintaxis

> /CLRHEADER *file*

### <a name="arguments"></a>Argumentos

*file*<br/>
Un archivo de imagen creado con [/CLR](clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Comentarios

**/ CLRHEADER** muestra información acerca de los encabezados de .NET utilizados en cualquier programa administrado. El resultado muestra la ubicación y tamaño, en bytes, del encabezado de .NET y secciones en el encabezado.

Solo el [/HEADERS](headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](gl-whole-program-optimization.md) opción del compilador.

Cuando **/CLRHEADER** se utiliza en un archivo que se compiló con/CLR, habrá un **encabezado clr:** sección en la salida de dumpbin. El valor de **marcas** indica que se utilizó la opción/clr:

- 0--/clr (la imagen puede contener código nativo).

Se puede comprobar mediante programación si una imagen se generó para common language runtime.  Para obtener más información, vea [Cómo: Determinar si una imagen es nativa o CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017. Código que debe ser "pura" o "segura" se debe pasar a C#.

## <a name="see-also"></a>Vea también

- [Opciones de DUMPBIN](dumpbin-options.md)
