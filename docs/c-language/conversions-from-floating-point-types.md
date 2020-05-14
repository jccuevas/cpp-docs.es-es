---
title: Conversiones de tipos de punto flotante
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998716"
---
# <a name="conversions-from-floating-point-types"></a>Conversiones de tipos de punto flotante

Un valor de punto flotante que se convierte a otro tipo de punto flotante no sufre ningún cambio en el valor si el valor original se puede representar exactamente en el tipo del resultado. Si el valor original es numérico, pero no se puede representar exactamente, el resultado es el siguiente valor más alto o más bajo que se puede representar. Vea [Límites en constantes de punto flotante](../c-language/limits-on-floating-point-constants.md) para el intervalo de tipos de punto flotante.

Un valor de punto flotante que se convierte en un tipo entero se trunca primero mediante el descarte de todo valor fraccionario. Si este valor truncado se puede representar en el tipo del resultado, el resultado debe ser ese valor. Cuando no se puede representar, el valor del resultado es indefinido.

**Específicos de Microsoft**

Los compiladores de Microsoft usan la representación binary32 de IEEE-754 para los valores de **float** y la representación binary64 para **long double** y **double**. Como **long double** y **double** usan la misma representación, tienen el mismo rango y precisión.

Cuando el compilador convierte un número de punto flotante **double** o **long double** a **float**, redondea el resultado de acuerdo con los controles de entorno de punto flotante, que tienen como valor predeterminado "redondear al más próximo, empatar en par". Si un valor numérico es demasiado alto o demasiado bajo para representarse como un valor numérico **float**, el resultado de la conversión es infinito positivo o negativo según el signo del valor original y se produce una excepción de desbordamiento, si está habilitada.

Al convertir a tipos enteros, el resultado de una conversión a un tipo menor que **long** es el resultado de convertir el valor a **long** y, luego, convertirlo al tipo del resultado.

Para la conversión a tipos enteros como mínimo tan grandes como **long**, la conversión de un valor demasiado alto o demasiado bajo para representarlo en el tipo del resultado puede devolver cualquiera de los siguientes valores:

- El resultado puede ser un *valor centinela*, que es el valor que se puede representar más alejado de cero. En el caso de los tipos con signo, es el valor más bajo que se puede representar (0x800...0). En el caso de los tipos sin signo, es el valor más alto que se puede representar (0xFF...F).

- El resultado puede ser *saturado*, donde los valores demasiado altos para representarse se convierten al valor más alto que se puede representar y los valores demasiado bajos para representarse se convierten al valor más bajo que se puede representar. Uno de estos dos valores también se usa como valor centinela.

- Para la conversión a **unsigned long** o **unsigned long long**, el resultado de convertir un valor fuera de intervalo puede ser un valor distinto del valor más alto o más bajo que se puede representar. El hecho de que el resultado sea un valor centinela o saturado depende de las opciones del compilador y de la arquitectura de destino. Las versiones futuras del compilador podrían devolver un valor saturado o centinela.

**FIN de Específicos de Microsoft**

En la tabla siguiente se resumen las conversiones de tipos de punto flotante.

## <a name="table-of-conversions-from-floating-point-types"></a>Tabla de conversiones de tipos de punto flotante

|De|En|Método|
|----------|--------|------------|
|**float**|**char**|Conversión a **long**; conversión de **long** a **char**|
|**float**|**short**|Conversión a **long**; conversión de **long** a **short**|
|**float**|**int**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **int**, el resultado es indefinido.|
|**float**|**long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|
|**float**|**long long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **long long**, el resultado es indefinido.|
|**float**|**unsigned char**|Conversión a **long**; conversión de **long** a **unsigned char**|
|**float**|**unsigned short**|Conversión a **long**; conversión de **long** a **unsigned short**|
|**float**|**unsigned**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned**, el resultado es indefinido.|
|**float**|**unsigned long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned long**, el resultado es indefinido.|
|**float**|**unsigned long long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned long long**, el resultado es indefinido.|
|**float**|**double**|Se representa como **double**.|
|**float**|**long double**|Se representa como **long double**.|
|**double**|**char**|Conversión a **float**; conversión de **float** a **char**|
|**double**|**short**|Conversión a **float**; conversión de **float** a **short**|
|**double**|**int**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **int**, el resultado es indefinido.|
|**double**|**long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|
|**double**|**unsigned char**|Conversión a **long**; conversión de **long** a **unsigned char**|
|**double**|**unsigned short**|Conversión a **long**; conversión de **long** a **unsigned short**|
|**double**|**unsigned**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned**, el resultado es indefinido.|
|**double**|**unsigned long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned long**, el resultado es indefinido.|
|**double**|**unsigned long long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned long long**, el resultado es indefinido.|
|**double**|**float**|Se representa como **float**. Si el valor **double** no se puede representar exactamente como **float**, se produce una pérdida de precisión. Si el valor es demasiado grande para representarse como **float**, el resultado es indefinido.|
|**double**|**long double**|El valor **long double** se trata como **double**.|

Las conversiones de **long double** siguen el mismo método que las conversiones de **double**.

## <a name="see-also"></a>Vea también

[Conversiones de asignación](../c-language/assignment-conversions.md)
