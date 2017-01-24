---
title: "String and Text Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "string classes [ATL]"
  - "conversión de cadenas, ATL"
ms.assetid: aa0cdc41-c953-4b17-82b6-59b908545571
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# String and Text Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases proporcionan compatibilidad para cadenas y las conversiones de cadena de texto.  
  
-   La clase de[CA2AEX](../atl/reference/ca2aex-class.md) This usan las macros `CA2TEX` y `CT2AEX`de la conversión de cadenas, y typedef **CA2A**.  
  
-   La clase de[CA2CAEX](../atl/reference/ca2caex-class.md) This usan las macros `CA2CTEX` y `CT2CAEX`de la conversión de cadenas, y typedef **CA2CA**.  
  
-   La clase de[CA2WEX](../atl/reference/ca2wex-class.md) This usan las macros `CA2TEX`, `CA2CTEX`, `CT2WEX`, y `CT2CWEX`, y typedef **CA2W**de la conversión de cadenas.  
  
-   La clase de[CW2AEX](../atl/reference/cw2aex-class.md) This usan las macros `CT2AEX`, `CW2TEX`, `CW2CTEX`, y `CT2CAEX`, y typedef **CW2A**de la conversión de cadenas.  
  
-   La clase de[CW2CWEX](../atl/reference/cw2cwex-class.md) This usan las macros `CW2CTEX` y `CT2CWEX`de la conversión de cadenas, y typedef **CW2CW**.  
  
-   La clase de[CW2WEX](../atl/reference/cw2wex-class.md) This usan las macros `CW2TEX` y `CT2WEX`de la conversión de cadenas, y typedef `CW2W`.  
  
-   La clase de[CComBSTR](../atl/reference/ccombstr-class.md) Esta es un contenedor para s para `BSTR`.  
  
-   La clase de adaptador de argumento de[\_U\_STRINGorID](../atl/reference/u-stringorid-class.md) This permite nombres de recursos \(s de`LPCTSTR`\) o los id. de recurso \(s de**UINT**\) que se pasarán a una función sin requerir que el llamador convertir el id. en una cadena mediante la macro de **MAKEINTRESOURCE** .  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)   
 [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)