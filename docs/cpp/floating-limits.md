---
title: "L&#237;mites flotantes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FLOAT.H (archivo de encabezado)"
  - "constantes de punto flotante, límites"
  - "números de punto flotante, límites flotantes"
  - "límites, constantes de punto flotante"
  - "intervalos, constantes de punto flotante"
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# L&#237;mites flotantes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 En la tabla siguiente se hace una lista de los límites de los valores de las constantes de punto flotante.  Estos límites también se definen en el archivo de encabezado estándar FLOAT.H.  
  
### Límites en constantes de punto flotante  
  
|Constante|Significado|Valor|  
|---------------|-----------------|-----------|  
|FLT\_DIG DBL\_DIG LDBL\_DIG|Número de dígitos, q, tal que un número de punto flotante con q dígitos decimales se puede redondear en una representación de punto flotante y se puede restablecer sin pérdida de precisión.|6 15 15|  
|FLT\_EPSILON DBL\_EPSILON LDBL\_EPSILON|Número positivo menor x, tal que x \+ 1,0 no es igual a 1,0.|1,192092896e–07F 2,2204460492503131e–016 2,2204460492503131e–016|  
|FLT\_GUARD||0|  
|FLT\_MANT\_DIG DBL\_MANT\_DIG LDBL\_MANT\_DIG|Número de dígitos en la base especificada por FLT\_RADIX en el significado de punto flotante.  La base es 2; por consiguiente, estos valores especifican los bits.|24 53 53|  
|FLT\_MAX DBL\_MAX LDBL\_MAX|Número de punto flotante máximo que se puede representar.|3,402823466e\+38F 1,7976931348623158e\+308 1,7976931348623158e\+308|  
|FLT\_MAX\_10\_EXP DBL\_MAX\_10\_EXP LDBL\_MAX\_10\_EXP|Entero máximo tal que 10 elevado a dicho número es un número de punto flotante que se puede representar.|38 308 308|  
|FLT\_MAX\_EXP DBL\_MAX\_EXP LDBL\_MAX\_EXP|Entero máximo tal que FLT\_RADIX elevado a dicho número es un número de punto flotante que se puede representar.|128 1024 1024|  
|FLT\_MIN DBL\_MIN LDBL\_MIN|Valor positivo mínimo.|1,175494351e–38F 2,2250738585072014e–308 2,2250738585072014e–308|  
|FLT\_MIN\_10\_EXP DBL\_MIN\_10\_EXP LDBL\_MIN\_10\_EXP|Entero negativo mínimo tal que 10 elevado a dicho número es un número de punto flotante que se puede representar.|–37<br /><br /> –307<br /><br /> –307|  
|FLT\_MIN\_EXP DBL\_MIN\_EXP LDBL\_MIN\_EXP|Entero negativo mínimo tal que FLT\_RADIX elevado a dicho número es un número de punto flotante que se puede representar.|–125<br /><br /> –1021<br /><br /> –1021|  
|FLT\_NORMALIZE||0|  
|FLT\_RADIX \_DBL\_RADIX \_LDBL\_RADIX|Base de representación de exponente.|2 2 2|  
|FLT\_ROUNDS \_DBL\_ROUNDS \_LDBL\_ROUNDS|Modo de redondeo para la adición de punto flotante.|1 \(próximo\) 1 \(próximo\) 1 \(próximo\)|  
  
> [!NOTE]
>  La información de la tabla puede ser diferente en versiones futuras del producto.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Límites de enteros](../cpp/integer-limits.md)