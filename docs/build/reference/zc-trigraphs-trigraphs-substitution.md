---
title: '/ Zc: trigraphs (sustitución de trígrafos) | Documentos de Microsoft'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e465b62944b360d6fdb09da1230f3353658437b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Sustitución de trígrafos)

Cuando **/Zc: trigraphs** se especifica, el compilador reemplaza una secuencia de caracteres de trígrafo utilizando un carácter de puntuación correspondiente.

## <a name="syntax"></a>Sintaxis

> **/ Zc: trigraphs**[**-**]  

## <a name="remarks"></a>Comentarios

A *trígrafos* está formada por dos signos de interrogación consecutivos ("??") seguido de un tercer carácter único. El estándar del lenguaje C admite trígrafos para archivos de origen que utilizan un juego de caracteres que no contenga representaciones gráficas adecuadas para algunos caracteres de puntuación. ¿Por ejemplo, cuando se habilitan los trígrafos, el compilador reemplaza el "? = "trígrafos mediante el carácter '#'. A través de C ++ 14, se admiten los trígrafos como en C. El estándar C ++ 17 quita trígrafos del lenguaje C++. En el código de C++, el **/Zc: trigraphs** opción del compilador habilita la sustitución de las secuencias de trígrafos por el carácter de puntuación correspondiente. **/Zc:trigraphs-** deshabilita la sustitución de trígrafos.

El **/Zc: trigraphs** opción está desactivada de forma predeterminada, y la opción no está afectado cuando el [/ permisivo-](permissive-standards-conformance.md) se especifica la opción.

Para obtener una lista de los trígrafos C/C++ y un ejemplo que muestra cómo usar trígrafos, vea [trígrafos](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zc: trigraphs** o **/Zc:trigraphs-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
[Trígrafos](../../c-language/trigraphs.md)<br/>
