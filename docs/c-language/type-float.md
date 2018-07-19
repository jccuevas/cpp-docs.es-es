---
title: Tipo float | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e218f7b5025de10dc06bf20fc759aed93189ec53
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390940"
---
# <a name="type-float"></a>Tipo float
Los números de punto flotante utilizan el formato IEEE (Institute of Electrical and Electronics Engineers). Los valores de precisión sencilla con el tipo float tienen 4 bytes, formados por un bit de signo, un exponente binario de 8 bits con exceso 127 y una mantisa de 23 bits. La mantisa representa un número entre 1,0 y 2,0. Puesto que el bit de alto nivel de la mantisa siempre es 1, no se almacena en el número. En esta representación se proporciona un intervalo de aproximadamente 3,4E-38 a 3,4E+38 para el tipo float.  
  
 Puede declarar variables como float o double, según las necesidades de la aplicación. Las diferencias principales entre los dos tipos son la precisión que pueden representar, el almacenamiento que requieren y su intervalo. En la tabla siguiente se muestra la relación entre los requisitos de precisión y almacenamiento.  
  
### <a name="floating-point-types"></a>Tipos de punto flotante  
  
|Tipo|Dígitos significativos|Número de bytes|  
|----------|------------------------|---------------------|  
|float|6 - 7|4|  
|double|15 - 16|8|  
  
 Las variables de punto flotante se representan mediante una mantisa, que contiene el valor del número y un exponente que contiene el orden de magnitud del número.  
  
 En la tabla siguiente se muestra el número de bits asignados a la mantisa y el exponente de cada tipo de punto flotante. El bit más significativo de cualquier tipo float o double es siempre el bit de signo. Si es 1, el número se considera negativo; en caso contrario, se considera un número positivo.  
  
### <a name="lengths-of-exponents-and-mantissas"></a>Longitud de exponentes y mantisas  
  
|Tipo|Longitud del exponente|Longitud de la mantisa|  
|----------|---------------------|---------------------|  
|float|8 bits|23 bits|  
|double|11 bits|52 bits|  
  
 Como los exponentes se almacenan en una forma sin signo, el exponente se reduce a la mitad de su valor posible. Para el tipo float, la diferencia es 127; para el tipo double, es 1023. Puede calcular el valor real del exponente restando el valor de diferencia del valor del exponente.  
  
 La mantisa se almacena como una fracción binaria mayor o igual que 1 y menor que 2. Para los tipos float y double, hay un 1 inicial implícito en la mantisa en la posición del bit más significativo, por lo que las mantisas tienen en realidad 24 y 53 bits de longitud, respectivamente, aunque el bit más significativo nunca se almacena en memoria.  
  
 En lugar del método de almacenamiento descrito, el paquete de puntos flotantes puede almacenar los números de punto flotante binarios como números desnormalizados. Los “números desnormalizados” son números de punto flotante distintos de cero con valores de exponente reservados en los que el bit más significativo de la mantisa es 0. Utilizando el formato desnormalizado, el intervalo de un número de punto flotante se puede extender a costa de la precisión. No se puede controlar si un número de punto flotante se representa en formato normalizado o desnormalizado; el paquete de puntos flotantes determina la representación. El paquete de puntos flotantes nunca utiliza una forma desnormalizada a menos que el exponente sea menor que el mínimo que se puede representar en una forma normalizada.  
  
 En la tabla siguiente se muestran los valores mínimo y máximo que se pueden almacenar en variables de cada tipo de punto flotante. Los valores mostrados en esta tabla se aplican solo a los números de punto flotante normalizados; los números de punto flotante desnormalizados tienen un valor mínimo menor. Tenga en cuenta que los números incluidos en registros de 80*x*87 siempre se representan en la forma normalizada de 80 bits; los números solo se pueden representar en la forma desnormalizada cuando se almacenan en variables de punto flotante de 32 bits o 64 bits (variables de tipo float y tipo long).  
  
### <a name="range-of-floating-point-types"></a>Intervalo de tipos de punto flotante  
  
|Tipo|Valor mínimo|Valor máximo|  
|----------|-------------------|-------------------|  
|flotante|1,175494351 E - 38|3,402823466 E + 38|  
|double|2,2250738585072014 E - 308|1,7976931348623158 E + 308|  
  
 Si la precisión no es tan importante como el almacenamiento, considere la posibilidad de usar el tipo float para las variables de punto flotante. Y a la inversa: si la precisión es el criterio más importante, use el tipo double.  
  
 Las variables de punto flotante se pueden promover a un tipo mas significativo (de tipo float a tipo double). La promoción se produce cuando se realizan operaciones aritméticas en variables de punto flotante. Estas operaciones aritméticas siempre se realizan con un grado tan alto de precisión como la variable con el máximo grado de precisión. Considere, por ejemplo, las siguientes declaraciones de tipo:  
  
```  
float f_short;  
double f_long;  
long double f_longer;  
  
f_short = f_short * f_long;  
```  
  
 En el ejemplo anterior, la variable `f_short` se promueve al tipo double y se multiplica por `f_long`; el resultado se redondea al tipo float antes de que se asigne a `f_short`.  
  
 En el ejemplo siguiente (que utiliza las declaraciones del ejemplo anterior), las operaciones aritméticas se realizan en la precisión float (32 bits) en las variables; el resultado se promueve entonces al tipo double:  
  
```  
f_longer = f_short * f_short;  
```  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)