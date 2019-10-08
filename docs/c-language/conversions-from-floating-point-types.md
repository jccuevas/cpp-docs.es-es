---
title: Conversiones de tipos de punto flotante
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998716"
---
# <a name="conversions-from-floating-point-types"></a>Conversiones de tipos de punto flotante

Un valor de punto flotante que se convierte en otro tipo de punto flotante no sufre ningún cambio en el valor si el valor original se va a representar exactamente en el tipo de resultado. Si el valor original es numérico, pero no se puede representar exactamente, el resultado es el siguiente valor más bajo o inferior que se puede representar. Vea [límites en las constantes de punto flotante](../c-language/limits-on-floating-point-constants.md) para el intervalo de tipos de punto flotante.

Un valor de punto flotante que se convierte en un tipo entero se trunca primero descartando cualquier valor fraccionario. Si este valor truncado se puede representar en el tipo de resultado, el resultado debe ser ese valor. Cuando no se represente, el valor del resultado es indefinido.

**Específicos de Microsoft**

Los compiladores de Microsoft usan la representación IEEE-754 binary32 para los valores **float** y la representación binary64 para **Long Double** y **Double**. Dado que **Long Double** y **Double** usan la misma representación, tienen el mismo rango y precisión.

Cuando el compilador convierte un **número de punto flotante Double o** **Long Double** en un valor **float**, redondea el resultado de acuerdo con los controles de entorno de punto flotante, que de forma predeterminada "redondear a más cercano, se vincula a par". Si un valor numérico es demasiado alto o demasiado bajo para representarse como un valor de **punto flotante** numérico, el resultado de la conversión es infinito positivo o negativo según el signo del valor original, y se produce una excepción de desbordamiento, si está habilitada.

Al convertir a tipos enteros, el resultado de una conversión a un tipo menor que **Long** es el resultado de convertir el valor en **Long**y, a continuación, convertirlo en el tipo de resultado.

Para la conversión a tipos enteros al menos tan grande como **Long**, una conversión de un valor demasiado alto o demasiado bajo para representarlo en el tipo de resultado puede devolver cualquiera de los siguientes valores:

- El resultado puede ser un *valor centinela*, que es el valor representable más alejado de cero. En el caso de los tipos con signo, es el valor representable más bajo (0x800... 0). En el caso de los tipos sin signo, es el valor más alto que se puede representar (0xFF... F).

- El resultado puede ser *saturado*, donde los valores demasiado altos para representar se convierten al valor representable más alto y los valores demasiado bajos para representarlos se convierten al valor más bajo que se puede representar. Uno de estos dos valores también se usa como el valor de centinela.

- Para la conversión a **Long sin signo** o **unsigned Long Long**, el resultado de convertir un valor fuera de intervalo puede ser un valor distinto del valor representable mayor o menor. Si el resultado es un valor Centinela o saturado o no depende de las opciones del compilador y de la arquitectura de destino. En su lugar, las versiones futuras del compilador pueden devolver un valor saturado o Sentinel.

**FIN de Específicos de Microsoft**

En la tabla siguiente se resumen las conversiones de tipos de punto flotante.

## <a name="table-of-conversions-from-floating-point-types"></a>Tabla de conversiones de tipos de punto flotante

|De|En|Método|
|----------|--------|------------|
|**float**|**char**|Conversión a **long**; conversión de **long** a **char**|
|**float**|**short**|Conversión a **long**; conversión de **long** a **short**|
|**float**|**int**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **int**, el resultado es indefinido.|
|**float**|**long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|
|**float**|**long long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **Long Long**, el resultado es undefined.|
|**float**|**unsigned char**|Convertir en **Long**; convertir **Long** en **Char sin signo**|
|**float**|**unsigned short**|Conversión a **long**; conversión de **long** a **unsigned short**|
|**float**|**unsigned**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **sin signo**, el resultado es indefinido.|
|**float**|**unsigned long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned Long**, el resultado es undefined.|
|**float**|**unsigned Long Long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned Long Long**, el resultado es undefined.|
|**float**|**double**|Se representa como un **valor Double**.|
|**float**|**long double**|Se representa como un **Long Double**.|
|**double**|**char**|Conversión a **float**; conversión de **float** a **char**|
|**double**|**short**|Conversión a **float**; conversión de **float** a **short**|
|**double**|**int**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **int**, el resultado es indefinido.|
|**double**|**long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **long**, el resultado es indefinido.|
|**double**|**unsigned char**|Convertir en **Long**; convertir **Long** en **Char sin signo**|
|**double**|**unsigned short**|Conversión a **long**; conversión de **long** a **unsigned short**|
|**double**|**unsigned**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **sin signo**, el resultado es indefinido.|
|**double**|**unsigned long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned Long**, el resultado es undefined.|
|**double**|**unsigned Long Long**|Trunca en el separador decimal. Si el resultado es demasiado grande para representarse como **unsigned Long Long**, el resultado es undefined.|
|**double**|**float**|Se representa como **float**. Si el valor **Double** no se puede representar exactamente como **float**, se produce una pérdida de precisión. Si el valor es demasiado grande para representarse como **float**, el resultado es indefinido.|
|**double**|**long double**|El valor **long double** se trata como **double**.|

Las conversiones de **Long Double** siguen el mismo método que las conversiones de **Double**.

## <a name="see-also"></a>Vea también

[Conversiones de asignación](../c-language/assignment-conversions.md)
