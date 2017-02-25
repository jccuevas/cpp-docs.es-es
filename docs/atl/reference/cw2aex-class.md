---
title: "CW2AEX (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CW2AEX<t_nBufferLength>"
  - "CW2AEX"
  - "ATL.CW2AEX<t_nBufferLength>"
  - "ATL::CW2AEX"
  - "ATL.CW2AEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CW2AEX (clase)"
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CW2AEX (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es utilizada por las macros `CT2AEX`, `CW2TEX`, `CW2CTEX`, y `CT2CAEX`, y typedef **CW2 A**de la conversión de cadenas.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CW2AEX  
```  
  
#### Parámetros  
 `t_nBufferLength`  
 El tamaño del búfer utilizado en el proceso de traducción.  la longitud predeterminada es 128 bytes.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2AEX::CW2AEX](../Topic/CW2AEX::CW2AEX.md)|el constructor.|  
|[CW2AEX::~CW2AEX](../Topic/CW2AEX::~CW2AEX.md)|El destructor.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2AEX::operator LPSTR](../Topic/CW2AEX::operator%20LPSTR.md)|operador de conversión.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2AEX::m\_psz](../Topic/CW2AEX::m_psz.md)|El miembro de datos que almacena la cadena de origen.|  
|[CW2AEX::m\_szBuffer](../Topic/CW2AEX::m_szBuffer.md)|el buffer estático, utilizado para almacenar la cadena convertida.|  
  
## Comentarios  
 A menos que sea adicional se requiere la funcionalidad, utilice `CT2AEX`, `CW2TEX`, `CW2CTEX`, `CT2CAEX`, o **CW2A** en el código.  
  
 Esta clase contiene un buffer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión.  Si el resultado es demasiado grande ajustarse al buffer estático, la clase asigna memoria mediante `malloc`, libera la memoria cuando el objeto salga del ámbito.  Esto garantiza que, a diferencia de las macros de conversión de texto disponible en versiones anteriores de ATL, esta clase es seguro utilizar en bucles y que no desbordará la pila.  
  
 Si los intentos de la clase para asignar memoria en la pila y se produce un error, se denominan `AtlThrow` con un argumento de **E\_OUTOFMEMORY**.  
  
 De forma predeterminada, las clases de conversión ATL y las macros utilizan la página de códigos ANSI actual del subproceso para la conversión.  Si desea invalidar ese comportamiento para una conversión determinada, especifique la página de códigos como segundo parámetro al constructor para la clase.  
  
 las macros siguientes se basan en esta clase:  
  
-   `CT2AEX`  
  
-   `CW2TEX`  
  
-   `CW2CTEX`  
  
-   `CT2CAEX`  
  
 Typedef siguiente está basada en esta clase:  
  
-   **CW2A**  
  
 Para consultar estas macros de conversión de texto, vea [Macros de conversión de cadena ATL y MFC](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md).  
  
## Ejemplo  
 Vea [Macros de conversión de cadena ATL y MFC](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) para obtener un ejemplo de cómo utilizar estas macros de la conversión de cadenas.  
  
## Requisitos  
 **encabezado:** atlconv.h  
  
## Vea también  
 [CA2AEX \(clase\)](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX \(clase\)](../../atl/reference/ca2caex-class.md)   
 [CA2WEX \(clase\)](../../atl/reference/ca2wex-class.md)   
 [CW2CWEX \(clase\)](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX \(clase\)](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)