---
title: "L&#237;mites de las constantes de punto flotante | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "constantes, punto flotante"
  - "FLOAT.H (archivo de encabezado)"
  - "constantes de punto flotante, límites"
  - "números de punto flotante, límites flotantes"
  - "límites, constantes de punto flotante"
  - "intervalos, constantes de punto flotante"
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# L&#237;mites de las constantes de punto flotante
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Los límites de los valores de las constantes de punto flotante se proporcionan en la tabla siguiente.  El archivo de encabezado FLOAT.H contiene esta información.  
  
### Límites en constantes de punto flotante  
  
|Constante|Significado|Valor|  
|---------------|-----------------|-----------|  
|**FLT\_DIGDBL\_DIGLDBL\_DIG**|Número de dígitos, *q*, tal que un número de punto flotante con *q* dígitos decimales se puede redondear en una representación de punto flotante y restablecer sin pérdida de precisión.|6 15 15|  
|**FLT\_EPSILONDBL\_EPSILONLDBL\_EPSILON**|El número positivo menor *x*, tal que *x* \+ 1,0 no es igual a 1,0|1,192092896e–07F 2,2204460492503131e–016 2,2204460492503131e–016|  
|**FLT\_GUARD**||0|  
|**FLT\_MANT\_DIGDBL\_MANT\_DIGLDBL\_MANT\_DIG**|Número de dígitos en la base especificada por **FLT\_RADIX** en el significado de punto flotante.  La base es 2; por consiguiente, estos valores especifican los bits.|24 53 53|  
|**FLT\_MAXDBL\_MAXLDBL\_MAX**|Número de punto flotante máximo que se puede representar.|3,402823466e\+38F 1,7976931348623158e\+308 1,7976931348623158e\+308|  
|**FLT\_MAX\_10\_EXPDBL\_MAX\_10\_EXPLDBL\_MAX\_10\_EXP**|Entero máximo tal que 10 elevado a dicho número es un número de punto flotante que se puede representar.|38 308 308|  
|**FLT\_MAX\_EXPDBL\_MAX\_EXPLDBL\_MAX\_EXP**|Entero máximo tal que **FLT\_RADIX** elevado a dicho número es un número de punto flotante que se puede representar.|128 1024 1024|  
|**FLT\_MINDBL\_MINLDBL\_MIN**|Valor positivo mínimo.|1,175494351e–38F 2,2250738585072014e–308 2,2250738585072014e–308|  
|**FLT\_MIN\_10\_EXPDBL\_MIN\_10\_EXPLDBL\_MIN\_10\_EXP**|Entero negativo mínimo tal que 10 elevado a dicho número es un número de punto flotante que se puede representar.|–37<br /><br /> –307<br /><br /> –307|  
|**FLT\_MIN\_EXPDBL\_MIN\_EXPLDBL\_MIN\_EXP**|Entero negativo mínimo tal que **FLT\_RADIX** elevado a dicho número es un número de punto flotante que se puede representar.|–125<br /><br /> –1021<br /><br /> –1021|  
|**FLT\_NORMALIZE**||0|  
|**FLT\_RADIX\_DBL\_RADIX\_LDBL\_RADIX**|Base de representación de exponente.|2 2 2|  
|**FLT\_ROUNDS\_DBL\_ROUNDS\_LDBL\_ROUNDS**|Modo de redondeo para la adición de punto flotante.|1 \(próximo\) 1 \(próximo\) 1 \(próximo\)|  
  
 Observe que la información de la tabla anterior puede diferir en futuras implementaciones.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Constantes de punto flotante de C](../c-language/c-floating-point-constants.md)