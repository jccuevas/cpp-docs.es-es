---
title: "CCustomTransition (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CCustomTransition"
  - "CCustomTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCustomTransition (clase)"
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CCustomTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una transición personalizada.  
  
## Sintaxis  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomTransition::CCustomTransition](../Topic/CCustomTransition::CCustomTransition.md)|Construye un objeto de transición personalizado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomTransition::Create](../Topic/CCustomTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
|[CCustomTransition::SetInitialValue](../Topic/CCustomTransition::SetInitialValue.md)|Establece un valor inicial, que se aplicará a una variable de animación asociada a esta transición.|  
|[CCustomTransition::SetInitialVelocity](../Topic/CCustomTransition::SetInitialVelocity.md)|Establece un progreso inicial, que se aplicará a una variable de animación asociada a esta transición.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomTransition::m\_bInitialValueSpecified](../Topic/CCustomTransition::m_bInitialValueSpecified.md)|Especifica si el valor inicial se especificó con SetInitialValue.|  
|[CCustomTransition::m\_bInitialVelocitySpecified](../Topic/CCustomTransition::m_bInitialVelocitySpecified.md)|Especifica si el progreso inicial se especificó con SetInitialVelocity.|  
|[CCustomTransition::m\_initialValue](../Topic/CCustomTransition::m_initialValue.md)|Almacena el valor inicial.|  
|[CCustomTransition::m\_initialVelocity](../Topic/CCustomTransition::m_initialVelocity.md)|Almacena el progreso inicial.|  
|[CCustomTransition::m\_pInterpolator](../Topic/CCustomTransition::m_pInterpolator.md)|Almacena un puntero en un interpolador personalizado.|  
  
## Comentarios  
 La clase CCustomTransitions permite a los desarrolladores implementar transiciones personalizadas.  Se ha creado y utilizado como una transición estándar, pero su constructor acepta como parámetro a un puntero a un interpolador personalizado.  Realice los siguientes pasos para utilizar una transición personalizada: 1.  Derive una clase de CCustomInterpolator e implemente al menos el método InterpolateValue.  2.  Asegúrese de que la vigencia del objeto interpolador personalizado debe ser mayor que la duración de la animación y donde se utiliza.  3.  Inicia \(mediante el nuevo operador\) un objeto CCustomTransition y pasa un puntero al interpolador personalizado en el constructor.  4.  Llame a CCustomTransition::SetInitialValue de la llamada y CCustomTransition::SetInitialVelocity si estos parámetros son necesarios para una interpolación personalizada.  5.  Pase el puntero de la transición personalizada al método AddTransition del objeto de animación, cuyo valor se debe animar con el algoritmo personalizado.  6.  Cuando el valor de objeto de animación debe cambiar, la API de Windows Animation llamará a InterpolateValue \(y otros métodos pertinentes\) en CCustomInterpolator.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CCustomTransition](../../mfc/reference/ccustomtransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)