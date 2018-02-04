---
title: "-volatile (interpretación de la palabra clave volatile) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
dev_langs:
- C++
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4528d53da01ae83f179f07ba52b2c86c335e883c
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interpretación de la palabra clave volatile)

Especifica cómo el [volátiles](../../cpp/volatile-cpp.md) palabra clave es que interpretarse.

## <a name="syntax"></a>Sintaxis

> **/volatile:**{**iso**|**ms**}  

## <a name="arguments"></a>Argumentos

**/volatile:iso**  
Selecciona estricta `volatile` semántica tal como se define en el lenguaje estándar ISO C++. No se garantiza que adquirir/liberación de semántica en accesos volátiles. Si el compilador está destinado a ARM, se trata de la interpretación predeterminada de `volatile`.

**/volatile:ms**  
Selecciona extendidas de Microsoft `volatile` semántica, que permiten agregar memoria garantías más allá del lenguaje C++ a la norma ISO de orden. Se garantiza que adquirir/liberación de semántica en accesos volátiles. Sin embargo, esta opción también obliga al compilador que genere barreras de memoria de hardware, lo que podrían producir una sobrecarga significativa en ARM y otras arquitecturas de ordenación de memoria débiles. Si el compilador tiene como destino cualquier plataforma excepto ARM, se trata de interpretación predeterminada de `volatile`.

## <a name="remarks"></a>Comentarios

Se recomienda encarecidamente que utilice **/volatile:iso** junto con las primitivas de sincronización explícita e intrínsecos del compilador al tratar con memoria que se comparte entre distintos subprocesos. Para obtener más información, consulte [volátiles](../../cpp/volatile-cpp.md).

Si migrar código existente o cambiar esta opción en el medio de un proyecto, puede resultar útil habilitar la advertencia [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) para identificar ubicaciones del código que se ven afectados por la diferencia en la semántica.

No hay ningún `#pragma` equivalente para controlar esta opción.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Para establecer el /volatile opción del compilador en Visual Studio

1. Abra la **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue **/volatile:iso** o **/volatile:ms** y, a continuación, elija **Aceptar** o **aplicar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[volatile](../../cpp/volatile-cpp.md)  
[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
