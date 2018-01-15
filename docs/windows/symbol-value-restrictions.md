---
title: "Restricciones de los valores de símbolos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.restrictions.value
dev_langs: C++
helpviewer_keywords:
- symbols, value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f2188d6904274fabce0f8626fa2f440ac324ff5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
-   El entorno de desarrollo de Visual Studio y MFC usan algunos intervalos numéricos para fines especiales. MFC se reserva todos los números con el bit más significativo establecido (de -32.768 a -1 o de 32.768 a 65.534, en función del signo).  
  
-   No se puede definir un valor de símbolo usando otras cadenas de símbolo. Por ejemplo, no se admite la siguiente definición de símbolo:  
  
    ```  
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported  
    ```  
  
-   No se puede usar macros de preprocesador con argumentos como definiciones de valor. Por ejemplo:  
  
    ```  
    #define   IDD_ABOUT  ID(7) //not supported  
    ```  
  
     no es una expresión válida, independientemente de cómo se evalúe `ID` en tiempo de compilación.  
  
-   La aplicación puede tener un archivo que contenga símbolos definidos con expresiones. Para obtener más información sobre cómo incluir los símbolos como símbolos de solo lectura, vea [símbolos utilizando compartidos (de sólo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md).  
  
 Para obtener más información sobre los intervalos numéricos, vea [TN023: recursos estándar de MFC](../mfc/tn023-standard-mfc-resources.md).  
  

  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Cambiar el valor numérico de un símbolo](../windows/changing-a-symbol-s-numeric-value.md)   
 [Restricciones de nombre de símbolo](../windows/symbol-name-restrictions.md)   
 [Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)