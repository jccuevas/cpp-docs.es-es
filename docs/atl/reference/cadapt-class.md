---
title: "CAdapt Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAdapt"
  - "ATL.CAdapt<T>"
  - "ATL::CAdapt"
  - "ATL::CAdapt<T>"
  - "CAdapt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& (operador), address-of (operador)"
  - "adapter objects"
  - "address-of (operador)"
  - "CAdapt class"
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAdapt Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta plantilla se utiliza para ajustar las clases que vuelven a definir el operador address\-of para devolver algo distinto de la dirección del objeto.  
  
## Sintaxis  
  
```  
  
      template <  
   class T  
>  
class CAdapt  
```  
  
#### Parámetros  
 `T`  
 El tipo adaptado.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAdapt::CAdapt](../Topic/CAdapt::CAdapt.md)|El constructor.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAdapt::operator const T&](../Topic/CAdapt::operator%20const%20T&.md)|Devuelve una referencia `const` a `m_T`.|  
|[CAdapt::operator T&](../Topic/CAdapt::operator%20T&.md)|Devuelve una referencia a `m_T`.|  
|[CAdapt::operator \<](../Topic/CAdapt::operator%20%3C.md)|Compara un objeto de tipo adaptado con `m_T`.|  
|[CAdapt::operator \=](../Topic/CAdapt::operator%20=.md)|Asigna un objeto del tipo adaptado a `m_T`.|  
|[CAdapt::operator \=\=](../Topic/CAdapt::operator%20==.md)|Compara un objeto de tipo adaptado con `m_T`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAdapt::m\_T](../Topic/CAdapt::m_T.md)|Datos que se están adaptando.|  
  
## Comentarios  
 `CAdapt` es una plantilla sencilla que se usa para ajustar las clases que vuelven a definir el operador address\-of \(`operator &`\) para devolver algo distinto de la dirección del objeto.  Algunos ejemplos de este tipo de clases son `CComBSTR`, `CComPtr` y `CComQIPtr` de ATL y la clase compatible con COM del compilador, `_com_ptr_t`.  Todas estas clases vuelven a definir el operador address\-of para devolver la dirección de uno de sus miembros de datos \(`BSTR` en el caso de `CComBSTR` y un puntero de interfaz en el caso de las demás clases\).  
  
 La función principal de `CAdapt` es ocultar el operador address\-of definido por la clase `T`, aunque mantiene las características de la clase adaptada.  `CAdapt` cumple esta función almacenando un miembro público, [m\_T](../Topic/CAdapt::m_T.md), de tipo `T` y definiendo operadores de conversión, operadores de comparación y un constructor de copias para permitir que las especializaciones de `CAdapt` se traten como si fueran objetos de tipo `T`.  
  
 La clase `CAdapt` del adaptador es útil porque algunas clases de estilo contenedor esperan poder obtener las direcciones de sus objetos contenidos utilizando el operador address\-of.  La nueva definición del operador address\-of puede frustrar este requisito, lo que normalmente produce errores de compilación e impide el uso del tipo no adaptado con clases que esperan que “simplemente funcione”.  `CAdapt` proporciona un mecanismo para evitar estos problemas.  
  
 Normalmente, utilizará `CAdapt` cuando desee almacenar objetos `CComBSTR`, `CComPtr`, `CComQIPtr` o `_com_ptr_t` en una clase de estilo contenedor.  Esta solía ser necesario en los contenedores de la biblioteca de C\+\+ estándar antes de la compatibilidad con C\+\+11 estándar, pero los contenedores de la biblioteca C\+\+11 estándar trabajan automáticamente con tipos que tienen un operador `operator&()` sobrecargado.  La biblioteca estándar logra esto utilizando internamente [std::addressof \(\)](../Topic/addressof.md) para obtener las direcciones reales de los objetos.  
  
## Requisitos  
 **Encabezado:** atlcomcli.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)