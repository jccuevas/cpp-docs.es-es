---
title: "Setting Up a Static Link to the Registrar Code (C++ Only) | Microsoft Docs"
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
  - "vincular [C++], to ATL Registrar code"
  - "statically linking to ATL Registrar code"
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Setting Up a Static Link to the Registrar Code (C++ Only)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los clientes de C\+\+ pueden establecer relaciones estáticas al código de registro.  Vinculación estática del analizador de registro agrega aproximadamente 5K a una versión de lanzamiento.  
  
 La manera más sencilla de configurar la vinculación estática supone que ha especificado [DECLARE\_REGISTRY\_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md) en la declaración del objeto.  \(Esta es la especificación predeterminada utilizada por el ATL\).  
  
### Para crear vínculos estáticas mediante DECLARE\_REGISTRY\_RESOURCEID  
  
1.  Especifique [\/D](../build/reference/d-preprocessor-definitions.md)`_ATL_STATIC_REGISTRY` en lugar de \/D**\_ATL\_DLL**.  
  
2.  Vuelva a compilar.  
  
## Vea también  
 [Componente de registro \(Registrador\)](../atl/atl-registry-component-registrar.md)