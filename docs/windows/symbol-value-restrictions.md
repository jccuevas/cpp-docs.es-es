---
title: Restricciones de los valores de símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.restrictions.value
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b174e46df7822ddf5ffbc747d0a7eb3cd71245e
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315410"
---
# <a name="symbol-value-restrictions"></a>Restricciones de los valores de símbolo

Un valor de símbolo puede ser cualquier entero expresado de la forma normal para las directivas de preprocesador #define. A continuación se muestran algunos ejemplos de valores de símbolo:

```
18
4001
0x0012
-3456
```

Los valores de símbolo de recursos (aceleradores, mapas de bits, cursores, cuadros de diálogo, iconos, menús, tablas de cadenas e información de versión) deben ser números decimales comprendidos en el intervalo de 0 a 32.767 (pero no pueden ser hexadecimales). Los valores de símbolo de partes de recursos, como los controles de cuadro de diálogo o las cadenas individuales de la tabla de cadenas, pueden ir de 0 a 65.534 o de -32.768 a 32.767.

Los símbolos de recursos son números de 16 bits. Puede especificarlos con o sin signo, pero se usan internamente como enteros sin signo. Así pues, los números negativos se convertirán a su valor positivo correspondiente.

A continuación se muestran algunas limitaciones de los valores de símbolo:

- El entorno de desarrollo de Visual Studio y MFC usan algunos intervalos numéricos para fines especiales. MFC se reserva todos los números con el bit más significativo establecido (de -32.768 a -1 o de 32.768 a 65.534, en función del signo).

- No se puede definir un valor de símbolo usando otras cadenas de símbolo. Por ejemplo, no se admite la siguiente definición de símbolo:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- No se puede usar macros de preprocesador con argumentos como definiciones de valor. Por ejemplo:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   no es una expresión válida, independientemente de cómo se evalúe `ID` en tiempo de compilación.

- La aplicación puede tener un archivo que contenga símbolos definidos con expresiones. Para obtener más información sobre cómo incluir los símbolos como símbolos de solo lectura, consulte [símbolos utilizando compartidos (de solo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md).

Para obtener más información sobre los intervalos numéricos, vea [TN023: recursos estándar de MFC](../mfc/tn023-standard-mfc-resources.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Cambio del valor numérico de un símbolo](../windows/changing-a-symbol-s-numeric-value.md)  
[Restricciones de los nombres de símbolo](../windows/symbol-name-restrictions.md)  
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)