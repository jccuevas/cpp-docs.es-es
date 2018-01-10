---
title: "Resumen de duración y visibilidad | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1ee45ec7a2a842cc45c01c0e6f43ab49ba55aa3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-lifetime-and-visibility"></a>Resumen de duración y visibilidad
En la tabla siguiente se muestra un resumen de características de duración y de visibilidad para la mayoría de los identificadores. Las tres primeras columnas proporcionan los atributos que definen duración y visibilidad. Un identificador con los atributos especificados por las tres primeras columnas tiene la duración y la visibilidad que se muestran en la cuarta y quinta columnas. Sin embargo, la tabla no cubre todos los casos posibles. Consulte [Clases de almacenamiento](../c-language/c-storage-classes.md) para obtener más información.  
  
### <a name="summary-of-lifetime-and-visibility"></a>Resumen de duración y visibilidad  
  
|Atributos:<br /><br /> Nivel|Elemento|Clase de almacenamiento<br /><br /> Especificador|Resultado: <br /><br /> Período de duración|Visibilidad|  
|---------------------------|----------|----------------------------------|--------------------------|----------------|  
|Ámbito de archivo|Definición de variable|**static**|Global|Resto del archivo de código fuente en el que aparece|  
||Declaración de variables|`extern`|Global|Resto del archivo de código fuente en el que aparece|  
||Prototipo o definición de función|**static**|Global|Archivo de código fuente único|  
||Prototipo de función|`extern`|Global|Resto del archivo de código fuente|  
|Ámbito de bloque|Declaración de variables|`extern`|Global|Bloque|  
||Definición de variable|**static**|Global|Bloque|  
||Definición de variable|**auto** o **register**|Local|Bloque|  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Description  
 En el ejemplo siguiente se ilustran los bloques, el anidamiento y la visibilidad de las variables:  
  
### <a name="code"></a>Código  
  
```  
// Lifetime_and_Visibility.c  
  
#include <stdio.h>  
  
int i = 1;  // i defined at external level  
  
int main()  // main function defined at external level  
{  
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)  
    {                                 // Begin first nested block  
        int i = 2, j = 3;          // i and j defined at internal level  
        printf_s( "%d %d\n", i, j );  // Prints 2, 3  
        {                             // Begin second nested block  
            int i = 0;                // i is redefined  
            printf_s( "%d %d\n", i, j ); // Prints 0, 3  
        }                             // End of second nested block  
        printf_s( "%d\n", i );        // Prints 2 (outer definition  
                                      //  restored)  
    }                                 // End of first nested block  
    printf_s( "%d\n", i );            // Prints 1 (external level  
                                      // definition restored)  
    return 0;  
}   
```  
  
### <a name="comments"></a>Comentarios  
 En este ejemplo, hay cuatro niveles de visibilidad: el nivel externo y tres niveles bloqueados. Los valores se imprimen en pantalla según se indica en los comentarios que siguen a cada instrucción.  
  
## <a name="see-also"></a>Vea también  
 [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md)