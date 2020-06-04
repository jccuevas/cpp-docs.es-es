---
title: /Zc:trigraphs (Sustitución de trígrafos)
ms.date: 03/06/2018
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 0e4c98e09551d39e3ff7978767b21f1d2c5bb318
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438655"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Sustitución de trígrafos)

Cuando se especifica **/Zc: trígrafos** , el compilador reemplaza una secuencia de caracteres de trígrafos mediante el carácter de puntuación correspondiente.

## <a name="syntax"></a>Sintaxis

> **/Zc: trígrafos**[ **-** ]

## <a name="remarks"></a>Observaciones

Un *trígrafo* se compone de dos signos de interrogación consecutivos ("??") seguidos de un tercer carácter único. El estándar del lenguaje C admite trígrafos para los archivos de código fuente que usan un juego de caracteres que no contiene representaciones gráficas adecuadas para algunos caracteres de puntuación. Por ejemplo, cuando se habilitan los trígrafos, el compilador reemplaza el = "trigraph mediante el carácter" # ". A través de C++ 14, se admiten trígrafos como en C. El estándar C++ 17 quita los C++ trígrafos del lenguaje. En C++ el código, la opción del compilador **/Zc: trigraphs** habilita la sustitución de secuencias de trígrafos por el carácter de puntuación correspondiente. **/Zc: trigraphies: deshabilita la sustitución de** trigraph.

La opción **/Zc: trigraphs** está desactivada de forma predeterminada y la opción no se ve afectada cuando se especifica la opción [/permissive-](permissive-standards-conformance.md) .

Para obtener una lista de CC++ /trígrafos y un ejemplo en el que se muestra cómo usar trígrafos, vea [trígrafos](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C/C++**  > **Línea de comandos**.

1. Modifique la propiedad **opciones adicionales** para incluir **/Zc: trígrafos** o **/Zc: trígrafos** y, después, elija **Aceptar**.

## <a name="see-also"></a>Consulte también

[/Zc (Ajuste)](zc-conformance.md)<br/>
[Trígrafos](../../c-language/trigraphs.md)<br/>
