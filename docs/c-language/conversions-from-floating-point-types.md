---
title: "Conversiones de tipos de punto flotante | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "convertir punto flotante"
  - "conversión de punto flotante"
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversiones de tipos de punto flotante
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un valor **float** convertido a **double** o a `long double`, o un valor **double** convertido a `long double`, no sufre ningún cambio de valor.  Un valor **double** convierte a un valor **float** se representa exactamente, si es posible.  Se puede perder precisión si el valor no se puede representar exactamente.  Si el resultado está fuera del intervalo, el comportamiento es indefinido.  Vea [Límites en constantes de punto flotante](../c-language/limits-on-floating-point-constants.md) para el intervalo de tipos de punto flotante.  
  
 Un valor flotante se convierte a un valor entero primero convirtiéndose primero a un valor **long** y, a continuación, del valor **long** al valor entero específico.  La parte decimal del valor flotante se descarta en la conversión a un valor **long**.  Si el resultado sigue siendo demasiado grande para caber en un valor **long**, el resultado de la conversión es indefinido.  
  
 **Específicos de Microsoft**  
  
 Cuando se convierte un número de punto flotante **double** o `long double` a un número de punto flotante más pequeño, el valor de la variable de punto flotante se trunca hacia cero cuando se produce un subdesbordamiento.  Un desbordamiento produce un error en tiempo de ejecución.  Observe que el compilador de Microsoft C asigna `long double` al tipo **double**.  
  
 **FIN de Específicos de Microsoft**  
  
 En la tabla siguiente se resumen las conversiones de tipos de punto flotante.  
  
### Conversiones de tipos de punto flotante  
  
|De|Para|Método|  
|--------|----------|------------|  
|**float**|`char`|Convierte a **long**; convierte **long** a `char`|  
|**float**|**short**|Convierte a **long**; convierte **long** a **short**|  
|**float**|**long**|Trunca en el separador decimal.  Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|  
|**float**|**unsigned short**|Convierte a **long**; convierte **long** a `unsigned` **short**|  
|**float**|`unsigned long`|Convierte a **long**; convierte **long** a `unsigned` **long**|  
|**float**|**double**|Cambia la representación interna|  
|**float**|`long double`|Cambia la representación interna|  
|**double**|`char`|Convierte a **float**; convierte **float** a `char`|  
|**double**|**short**|Convierte a **float**; convierte **float** a **short**|  
|**double**|**long**|Trunca en el separador decimal.  Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|  
|**double**|**unsigned short**|Convierte a **long**; convierte **long** a **unsigned short**|  
|**double**|`unsigned long`|Convierte a **long**; convierte **long** a `unsigned` **long**|  
|**double**|**float**|Se representa como **float**.  Si el valor **double** no se puede representar exactamente como **float**, se produce una pérdida de precisión.  Si el valor es demasiado grande para representarse como **float**, el resultado es indefinido.|  
|`long double`|`char`|Convierte a **float**; convierte **float** a `char`|  
|`long double`|**short**|Convierte a **float**; convierte **float** a **short**|  
|`long double`|**long**|Trunca en el separador decimal.  Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|  
|`long double`|**unsigned short**|Convierte a **long**; convierte **long** a `unsigned` **short**|  
|`long double`|`unsigned long`|Convierte a **long**; convierte **long** a `unsigned` **long**|  
|`long double`|**float**|Se representa como **float**.  Si el valor **double** no se puede representar exactamente como **float**, se produce una pérdida de precisión.  Si el valor es demasiado grande para representarse como **float**, el resultado es indefinido.|  
|`long double`|**double**|El valor **long double** se trata como **double**.|  
  
 Las conversiones de valores **float**, **double** o `long double` a `unsigned long` no son exactas si el valor que se está convirtiendo es mayor que el valor **long** positivo máximo.  
  
## Vea también  
 [Conversiones de asignación](../c-language/assignment-conversions.md)