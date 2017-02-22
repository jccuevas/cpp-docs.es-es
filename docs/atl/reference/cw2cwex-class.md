---
title: "CW2CWEX (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CW2CWEX"
  - "ATL::CW2CWEX"
  - "ATL.CW2CWEX"
  - "ATL.CW2CWEX<t_nBufferLength>"
  - "ATL::CW2CWEX<t_nBufferLength>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CW2CWEX (clase)"
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CW2CWEX (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es utilizada por las macros `CW2CTEX` y `CT2CWEX`de la conversión de cadenas, y typedef `CW2W`.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CW2CWEX  
```  
  
#### Parámetros  
 `t_nBufferLength`  
 El tamaño del búfer utilizado en el proceso de traducción.  la longitud predeterminada es 128 bytes.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2CWEX::CW2CWEX](../Topic/CW2CWEX::CW2CWEX.md)|el constructor.|  
|[CW2CWEX::~CW2CWEX](../Topic/CW2CWEX::~CW2CWEX.md)|El destructor.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2CWEX::operator LPCWSTR](../Topic/CW2CWEX::operator%20LPCWSTR.md)|operador de conversión.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2CWEX::m\_psz](../Topic/CW2CWEX::m_psz.md)|El miembro de datos que almacena la cadena de origen.|  
  
## Comentarios  
 a menos que se requiera la funcionalidad adicional, utilice `CW2CTEX`, `CT2CWEX`, o `CW2W` en el código.  
  
 Esta clase es seguro utilizar en bucles y no desbordará la pila.  De forma predeterminada, las clases de conversión ATL y las macros utilizan la página de códigos ANSI actual del subproceso para la conversión.  
  
 las macros siguientes se basan en esta clase:  
  
-   `CW2CTEX`  
  
-   `CT2CWEX`  
  
 Typedef siguiente está basada en esta clase:  
  
-   `CW2W`  
  
 Para consultar estas macros de conversión de texto, vea [Macros de conversión de cadena ATL y MFC](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md).  
  
## Ejemplo  
 Vea [Macros de conversión de cadena ATL y MFC](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) para obtener un ejemplo de cómo utilizar estas macros de la conversión de cadenas.  
  
## Requisitos  
 **encabezado:** atlconv.h  
  
## Vea también  
 [CA2AEX \(clase\)](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX \(clase\)](../../atl/reference/ca2caex-class.md)   
 [CA2WEX \(clase\)](../../atl/reference/ca2wex-class.md)   
 [CW2AEX \(clase\)](../../atl/reference/cw2aex-class.md)   
 [CW2WEX \(clase\)](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)