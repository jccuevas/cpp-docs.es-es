---
title: Conversiones de tipos de punto flotante | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce86a9ceffaa5d9dacfe56e6b89b677b3abb1517
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392489"
---
# <a name="conversions-from-floating-point-types"></a>Conversiones de tipos de punto flotante

Un valor **float** convertido a **double** o a **long double**, o un valor **double** convertido a **long double**, no sufre ningún cambio de valor. Un valor **double** convertido a un valor **float** se representa de forma exacta, si es posible. Se puede perder precisión si el valor no se puede representar exactamente. Si el resultado está fuera del intervalo, el comportamiento es indefinido. Vea [Límites en constantes de punto flotante](../c-language/limits-on-floating-point-constants.md) para el intervalo de tipos de punto flotante.

Un valor flotante se convierte a un valor entero convirtiéndolo primero a un valor **long** y, después, del valor **long** al valor entero específico. La parte decimal del valor flotante se descarta en la conversión a un valor **long**. Si el resultado sigue siendo demasiado grande para caber en un valor **long**, el resultado de la conversión es indefinido.

**Específicos de Microsoft**

Cuando se convierte un número de punto flotante **double** o **long double** a un número de punto flotante más pequeño, el valor de la variable de punto flotante se trunca hacia cero cuando se produce un subdesbordamiento. Un desbordamiento produce un error en tiempo de ejecución. Tenga en cuenta que el Compilador de Microsoft Visual C++ asigna **long double** al tipo **double**.

**FIN de Específicos de Microsoft**

En la tabla siguiente se resumen las conversiones de tipos de punto flotante.

## <a name="conversions-from-floating-point-types"></a>Conversiones de tipos de punto flotante

|De|En|Método|
|----------|--------|------------|
|**float**|**char**|Conversión a **long**; conversión de **long** a **char**|
|**float**|**short**|Conversión a **long**; conversión de **long** a **short**|
|**float**|**long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|
|**float**|**unsigned short**|Conversión a **long**; conversión de **long** a **unsigned short**|
|**float**|**unsigned long**|Conversión a **long**; conversión de **long** a **unsigned long**|
|**float**|**double**|Cambia la representación interna|
|**float**|**long double**|Cambia la representación interna|
|**double**|**char**|Conversión a **float**; conversión de **float** a **char**|
|**double**|**short**|Conversión a **float**; conversión de **float** a **short**|
|**double**|**long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|
|**double**|**unsigned short**|Conversión a **long**; conversión de **long** a **unsigned short**|
|**double**|**unsigned long**|Conversión a **long**; conversión de **long** a **unsigned long**|
|**double**|**float**|Se representa como **float**. Si el valor **double** no se puede representar exactamente como **float**, se produce una pérdida de precisión. Si el valor es demasiado grande para representarse como **float**, el resultado es indefinido.|
|**long double**|**char**|Conversión a **float**; conversión de **float** a **char**|
|**long double**|**short**|Conversión a **float**; conversión de **float** a **short**|
|**long double**|**long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|
|**long double**|**unsigned short**|Conversión a **long**; conversión de **long** a **unsigned short**|
|**long double**|**unsigned long**|Conversión a **long**; conversión de **long** a **unsigned long**|
|**long double**|**float**|Se representa como **float**. Si el valor **double** no se puede representar exactamente como **float**, se produce una pérdida de precisión. Si el valor es demasiado grande para representarse como **float**, el resultado es indefinido.|
|**long double**|**double**|El valor **long double** se trata como **double**.|

Las conversiones de valores **float**, **double** o **long double** a **unsigned long** no son exactas si el valor que se está convirtiendo es mayor que el valor **long** positivo máximo.

## <a name="see-also"></a>Vea también

[Conversiones de asignación](../c-language/assignment-conversions.md)  
