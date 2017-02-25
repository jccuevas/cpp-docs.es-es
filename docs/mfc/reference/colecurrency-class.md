---
title: "COleCurrency Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CURRENCY"
  - "COleCurrency"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleCurrency class"
  - "CURRENCY"
  - "fixed-point numbers"
  - "números, fixed-point"
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleCurrency Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

encapsula el tipo de datos de `CURRENCY` de automatización OLE.  
  
## Sintaxis  
  
```  
class COleCurrency  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleCurrency::COleCurrency](../Topic/COleCurrency::COleCurrency.md)|Crea un objeto `COleCurrency`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleCurrency::Format](../Topic/COleCurrency::Format.md)|Genera una representación de cadena con formato de un objeto de `COleCurrency` .|  
|[COleCurrency::GetStatus](../Topic/COleCurrency::GetStatus.md)|obtiene el estado \(validez\) de este objeto de `COleCurrency` .|  
|[COleCurrency::ParseCurrency](../Topic/COleCurrency::ParseCurrency.md)|Lee un valor de **CURRENCY** de una cadena y establece el valor de `COleCurrency`.|  
|[COleCurrency::SetCurrency](../Topic/COleCurrency::SetCurrency.md)|establece el valor de este objeto de `COleCurrency` .|  
|[COleCurrency::SetStatus](../Topic/COleCurrency::SetStatus.md)|Establece el estado \(validez\) para este objeto de `COleCurrency` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operador \=](../Topic/COleCurrency::operator%20=.md)|copia un valor de `COleCurrency` .|  
|[operador \+, \-](../Topic/COleCurrency::operator%20+,%20-.md)|Add, subtract, y signo de los valores de `COleCurrency` .|  
|[operador \+\=, \- \=](../Topic/COleCurrency::operator%20+=,%20-=.md)|Suma y resta un valor de `COleCurrency` de este objeto de `COleCurrency` .|  
|[operador \*,\/](../Topic/COleCurrency::operator%20*,%20-.md)|Escala un valor de `COleCurrency` por un valor entero.|  
|[\*\= de operador,\/\=](../Topic/COleCurrency::operator%20*=,%20-=.md)|Escala este valor de `COleCurrency` por un valor entero.|  
|[operador \<\<](../Topic/COleCurrency::operator%20%3C%3C,%20%3E%3E.md)|Genera un valor de `COleCurrency` a `CArchive` o a `CDumpContext`.|  
|[operador \>\>](../Topic/COleCurrency::operator%20%3C%3C,%20%3E%3E.md)|Entra en un objeto de `COleCurrency` de `CArchive`.|  
|[DIVISA de operador](../Topic/COleCurrency::operator%20CURRENCY.md)|Convierte un valor de `COleCurrency` en **CURRENCY**.|  
|[operator \=\=, \<, \<\=, etc..](../Topic/COleCurrency%20Relational%20Operators.md)|compara dos valores de `COleCurrency` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleCurrency::m\_cur](../Topic/COleCurrency::m_cur.md)|Contiene **CURRENCY** subyacente para este objeto de `COleCurrency` .|  
|[COleCurrency::m\_status](../Topic/COleCurrency::m_status.md)|contiene el estado de este objeto de `COleCurrency` .|  
  
## Comentarios  
 **COleCurrency** no tiene una clase base.  
  
 **CURRENCY** se implementa como 8 byte, valor entero de two's\- complemento escalado por 10.000.  Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y 4 dígitos a la derecha.  El tipo de datos de moneda es muy útil para los cálculos que implican dinero, o para los cálculos de punto fijo cuando es importante la exactitud.  Es uno de los tipos posibles para el tipo de datos de `VARIANT` de automatización OLE.  
  
 **COleCurrency** también implementa algunas operaciones aritméticas básicas para este tipo de punto fijo.  Las operaciones admitidas se han seleccionado controlar los errores que redondeaban realizadas cálculos de punto fijo.  
  
## Jerarquía de herencia  
 `COleCurrency`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)