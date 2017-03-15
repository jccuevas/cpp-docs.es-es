---
title: "moneypunct (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "moneypunct"
  - "std.moneypunct"
  - "xlocmon/std::moneypunct"
  - "std::moneypunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "moneypunct (clase)"
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# moneypunct (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que puede actuar como una faceta de configuración regional para describir las secuencias de tipo `CharType` usadas para representar un campo monetario de entrada o un campo monetario de salida.  Si el parámetro de plantilla `Intl` es `true`, se respetan las convenciones internacionales.  
  
## Sintaxis  
  
```  
template<class CharType, bool Intl>   
   class moneypunct;  
```  
  
#### Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar caracteres.  
  
 `Intl`  
 Una marca que especifica si las convenciones internacionales deben respetarse.  
  
## Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero.  El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
 El objeto estático constante intl almacena el valor del parámetro de plantilla **Intl**.  
  
### Constructores  
  
|||  
|-|-|  
|[moneypunct](../Topic/moneypunct::moneypunct.md)|Constructor de objetos de tipo `moneypunct`.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/moneypunct::char_type.md)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[string\_type](../Topic/moneypunct::string_type.md)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[curr\_symbol](../Topic/moneypunct::curr_symbol.md)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de moneda.|  
|[decimal\_point](../Topic/moneypunct::decimal_point.md)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como separador decimal.|  
|[do\_curr\_symbol](../Topic/moneypunct::do_curr_symbol.md)|Una función miembro virtual protegida que devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de moneda.|  
|[do\_decimal\_point](../Topic/moneypunct::do_decimal_point.md)|Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de separador decimal.|  
|[do\_frac\_digits](../Topic/moneypunct::do_frac_digits.md)|La función miembro virtual protegida devuelve un recuento específico de la configuración regional de la cantidad de dígitos que se muestran a la derecha de cualquier separador decimal.|  
|[do\_grouping](../Topic/moneypunct::do_grouping.md)|La función miembro virtual protegida devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.|  
|[do\_neg\_format](../Topic/moneypunct::do_neg_format.md)|Una función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional para dar formato a resultados con cantidades negativas.|  
|[do\_negative\_sign](../Topic/moneypunct::do_negative_sign.md)|Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo negativo.|  
|[do\_pos\_format](../Topic/moneypunct::do_pos_format.md)|Una función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional para dar formato a resultados con cantidades positivas.|  
|[do\_positive\_sign](../Topic/moneypunct::do_positive_sign.md)|Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo positivo.|  
|[do\_thousands\_sep](../Topic/moneypunct::do_thousands_sep.md)|Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de separador de miles.|  
|[frac\_digits](../Topic/moneypunct::frac_digits.md)|Devuelve un recuento específico de la configuración regional de la cantidad de dígitos que se muestran a la derecha del separador decimal.|  
|[agrupar](../Topic/moneypunct::grouping.md)|Devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda del separador decimal.|  
|[neg\_format](../Topic/moneypunct::neg_format.md)|Devuelve una regla específica de la configuración regional para dar formato a resultados con cantidades negativas.|  
|[negative\_sign](../Topic/moneypunct::negative_sign.md)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo negativo.|  
|[pos\_format](../Topic/moneypunct::pos_format.md)|Devuelve una regla específica de la configuración regional para dar formato a resultados con cantidades positivas.|  
|[positive\_sign](../Topic/moneypunct::positive_sign.md)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo positivo.|  
|[thousands\_sep](../Topic/moneypunct::thousands_sep.md)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de separador de miles.|  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<locale\>](../standard-library/locale.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)