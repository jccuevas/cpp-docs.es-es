---
title: "Allocating and Releasing Memory for a BSTR | Microsoft Docs"
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
  - "bstr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BSTR, asignación de memoria"
  - "memoria [C++], liberación"
  - "asignación de memoria, BSTR"
  - "memory deallocation, BSTR memory"
  - "memory deallocation, string memory"
  - "cadenas [C++], liberación"
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Allocating and Releasing Memory for a BSTR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al crear s para `BSTR`y las pasa entre los objetos COM, debe tener cuidado de tratar la memoria que utilizan para evitar pérdidas de memoria.  Cuando `BSTR` permanece dentro de una interfaz, debe liberar la memoria cuando termine con él.  Sin embargo, cuando `BSTR` pasa de una interfaz, el objeto receptor asume la responsabilidad de la administración de memoria.  
  
 Normalmente las reglas para asignar y liberar memoria asignada para s para `BSTR`son los siguientes:  
  
-   Cuando se llama a una función que espera un argumento de `BSTR` , debe asignar memoria para `BSTR` antes de la llamada y que el mercadola después.  Por ejemplo:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_1.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_2.cpp)]  
  
-   Cuando se llama a una función que devuelve `BSTR`, debe liberar la cadena personalmente.  Por ejemplo:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_3.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_4.cpp)]  
  
-   Al implementar una función que devuelve `BSTR`, asigna la cadena pero no la libere.  Recibir los lanzamientos desde la función memoria.  Por ejemplo:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_5.cpp)]  
  
## Vea también  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md)   
 [SysAllocString](http://msdn.microsoft.com/es-es/9e0437a2-9b4a-4576-88b0-5cb9d08ca29b)   
 [SysFreeString](http://msdn.microsoft.com/es-es/8f230ee3-5f6e-4cb9-a910-9c90b754dcd3)