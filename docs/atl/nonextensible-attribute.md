---
title: "nonextensible Attribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "nonextensible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces duales, nonextensible attribute"
  - "nonextensible attribute"
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nonextensible Attribute
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si una interfaz dual no es extendida en tiempo de ejecución \(es decir, no proporcionarán métodos o propiedades mediante **IDispatch::Invoke** que no están disponibles a través del vtable\), debe aplicar el atributo de **nonextensible** a la definición de interfaz.  Este atributo proporciona a los lenguajes de cliente \(como Visual Basic\) que se pueden utilizar para habilitar la comprobación completa del código en tiempo de compilación.  Si no se proporciona este atributo, pueden seguir ocultos en el código de cliente hasta el tiempo de ejecución.  
  
 Para obtener más información sobre el atributo de **nonextensible** y un ejemplo, vea [nonextensible](../Topic/nonextensible.md).  
  
## Vea también  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)