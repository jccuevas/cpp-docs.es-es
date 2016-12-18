---
title: "CComCurrency Class | Microsoft Docs"
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
  - "CComCurrency"
  - "ATL.CComCurrency"
  - "ATL::CComCurrency"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCurrency class"
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCurrency Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComCurrency` tiene métodos y operadores para crear y administrar un objeto CURRENCY.  
  
## Sintaxis  
  
```  
  
class CComCurrency  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCurrency::CComCurrency](../Topic/CComCurrency::CComCurrency.md)|El constructor para un objeto `CComCurrency`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCurrency::GetCurrencyPtr](../Topic/CComCurrency::GetCurrencyPtr.md)|Devuelve la dirección de un miembro de datos `m_currency`.|  
|[CComCurrency::GetFraction](../Topic/CComCurrency::GetFraction.md)|Llame a este método para devolver el componente de fracción de un objeto `CComCurrency`.|  
|[CComCurrency::GetInteger](../Topic/CComCurrency::GetInteger.md)|Llame a este método para devolver el componente entero de un objeto `CComCurrency`.|  
|[CComCurrency::Round](../Topic/CComCurrency::Round.md)|Llame a este método para redondear un objeto `CComCurrency` al valor entero más cercano.|  
|[CComCurrency::SetFraction](../Topic/CComCurrency::SetFraction.md)|Llame a este método para establecer el componente de fracción de un objeto `CComCurrency`.|  
|[CComCurrency::SetInteger](../Topic/CComCurrency::SetInteger.md)|Llame a este método para establecer el componente entero de un objeto `CComCurrency`.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCurrency::operator \-](../Topic/CComCurrency::operator%20-2.md)|Este operador se usa para restar en un objeto `CComCurrency`.|  
|[CComCurrency::operator \!\=](../Topic/CComCurrency::operator%20!=.md)|Compara dos objetos `CComCurrency` para determinar si no son iguales.|  
|[CComCurrency::operator \*](../Topic/CComCurrency::operator%20*.md)|Este operador se usa para multiplicar en un objeto `CComCurrency`.|  
|[CComCurrency::operator \*\=](../Topic/CComCurrency::operator%20*=.md)|Este operador se usa para multiplicar en un objeto `CComCurrency` y asignarle el resultado.|  
|[CComCurrency::operator \/](../Topic/CComCurrency::operator%20-1.md)|Este operador se usa para dividir en un objeto `CComCurrency`.|  
|[CComCurrency::operator \/\=](../Topic/CComCurrency::operator%20-=2.md)|Este operador se utiliza para dividir en un objeto `CComCurrency` y asignarle el resultado.|  
|[CComCurrency::operator \+](../Topic/CComCurrency::operator%20+.md)|Este operador se usa para sumar en un objeto `CComCurrency`.|  
|[CComCurrency::operator \+\=](../Topic/CComCurrency::operator%20+=.md)|Este operador se usa para sumar en un objeto `CComCurrency` y asignar el resultado al objeto actual.|  
|[CComCurrency::operator \<](../Topic/CComCurrency::operator%20%3C.md)|Este operador compara dos objetos `CComCurrency` para determinar el menor.|  
|[CComCurrency::operator \<\=](../Topic/CComCurrency::operator%20%3C=.md)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el menor.|  
|[CComCurrency::operator \=](../Topic/CComCurrency::operator%20=.md)|El operador asigna el objeto `CComCurrency` a un nuevo valor.|  
|[CComCurrency::operator \-\=](../Topic/CComCurrency::operator%20-=1.md)|Este operador se usa para restar en un objeto `CComCurrency` y asignarle el resultado.|  
|[CComCurrency::operator \=\=](../Topic/CComCurrency::operator%20==.md)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales.|  
|[CComCurrency::operator \>](../Topic/CComCurrency::operator%20%3E.md)|Este operador compara dos objetos `CComCurrency` para determinar el mayor.|  
|[CComCurrency::operator \>\=](../Topic/CComCurrency::operator%20%3E=.md)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el mayor.|  
|[CComCurrency::operator CURRENCY](../Topic/CComCurrency::operator%20CURRENCY.md)|Convierte un objeto `CURRENCY`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCurrency::m\_currency](../Topic/CComCurrency::m_currency.md)|La variable `CURRENCY` creada por la instancia de clase.|  
  
## Comentarios  
 `CComCurrency` es un contenedor para el tipo de datos **CURRENCY**.  **CURRENCY** se implementa como un valor entero de 8 bytes de dos complementos escalado por 10.000.  Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha.  El tipo de datos **CURRENCY** es muy útil para cálculos monetarios o para los cálculos de punto fijo, donde la precisión es importante.  
  
 El contenedor **CComCurrency** implementa operaciones aritméticas, de asignación y de comparación para este tipo de punto fijo.  Las aplicaciones compatibles se han seleccionado para controlar los errores de redondeo que se pueden producir durante los cálculos de punto fijo.  
  
 El objeto `CComCurrency` da acceso a los números situados a ambos lados del separador decimal en forma de dos componentes: un componente de número entero que almacena el valor situado a la izquierda del separador decimal y un componente de fracción que almacena el valor situado a la derecha del separador decimal.  El componente de fracción se almacena internamente como un valor entero entre \-9.999 \(**CY\_MIN\_FRACTION**\) y \+9.999 \(**CY\_MAX\_FRACTION**\).  El método [CComCurrency::GetFraction](../Topic/CComCurrency::GetFraction.md) devuelve un valor escalado por un factor de 10.000 \(**CY\_SCALE**\).  
  
 Al especificar los componentes entero y de fracción de un objeto **CComCurrency**, recuerde que el componente de fracción es un número de 0 a 9.999.  Esto es importante cuando se trata de una divisa como el dólar estadounidense, que expresa cantidades con solo dos dígitos después del separador decimal.  Aunque no se muestren los últimos dos dígitos, se deben tener en cuenta.  
  
|Valor|Posibles asignaciones CComCurrency|  
|-----------|----------------------------------------|  
|$10.50|CComCurrency\(10,5000\) *o* CComCurrency\(10.50\)|  
|$10.05|CComCurrency\(10,5000\) *o* CComCurrency\(10.50\)|  
  
 Los valores **CY\_MIN\_FRACTION**, **CY\_MAX\_FRACTION** y **CY\_SCALE** se definen en atlcur.h.  
  
## Requisitos  
 **Encabezado:** atlcur.h  
  
## Vea también  
 [COleCurrency Class](../../mfc/reference/colecurrency-class.md)   
 [CURRENCY](http://msdn.microsoft.com/es-es/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [Class Overview](../../atl/atl-class-overview.md)