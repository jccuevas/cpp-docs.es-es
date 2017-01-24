---
title: "CA2CAEX (clase) | Microsoft Docs"
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
  - "ATL.CA2CAEX"
  - "ATL.CA2CAEX<t_nBufferLength>"
  - "ATLCONV/CA2CAEX"
  - "ATL::CA2CAEX<t_nBufferLength>"
  - "ATL::CA2CAEX"
  - "CA2CAEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CA2CAEX (clase)"
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CA2CAEX (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es utilizada por las macros `CA2CTEX` y `CT2CAEX`de la conversión de cadenas, y typedef **CA2 CA**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CA2CAEX  
```  
  
#### Parámetros  
 `t_nBufferLength`  
 El tamaño del búfer utilizado en el proceso de traducción.  la longitud predeterminada es 128 bytes.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CA2CAEX::CA2CAEX](../Topic/CA2CAEX::CA2CAEX.md)|el constructor.|  
|[CA2CAEX::~CA2CAEX](../Topic/CA2CAEX::~CA2CAEX.md)|El destructor.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CA2CAEX::operator LPCSTR](../Topic/CA2CAEX::operator%20LPCSTR.md)|operador de conversión.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CA2CAEX::m\_psz](../Topic/CA2CAEX::m_psz.md)|El miembro de datos que almacena la cadena de origen.|  
  
## Comentarios  
 A menos que sea adicional se requiere la funcionalidad, utilice `CA2CTEX`, `CT2CAEX`, o **CA2CA** en su propio código.  
  
 Esta clase es seguro utilizar en bucles y no desbordará la pila.  De forma predeterminada, las clases de conversión ATL y las macros utilizarán la página de códigos ANSI actual del subproceso para la conversión.  
  
 las macros siguientes se basan en esta clase:  
  
-   `CA2CTEX`  
  
-   `CT2CAEX`  
  
 Typedef siguiente está basada en esta clase:  
  
-   **CA2CA**  
  
 Para consultar estas macros de conversión de texto, vea [Macros de conversión de cadena ATL y MFC](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md).  
  
## Ejemplo  
 Vea [Macros de conversión de cadena ATL y MFC](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) para obtener un ejemplo de cómo utilizar estas macros de la conversión de cadenas.  
  
## Requisitos  
 **encabezado:** atlconv.h  
  
## Vea también  
 [CA2AEX \(clase\)](../../atl/reference/ca2aex-class.md)   
 [CA2WEX \(clase\)](../../atl/reference/ca2wex-class.md)   
 [CW2AEX \(clase\)](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX \(clase\)](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX \(clase\)](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)