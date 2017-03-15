---
title: "Design Principles for Collection and Enumerator Interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collection interfaces"
  - "enumerator interfaces"
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Design Principles for Collection and Enumerator Interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay diferentes principios de diseño subyacente de cada tipo de interfaz:  
  
-   Una interfaz de intercalación proporciona *acceso aleatorio* *a un solo elemento* en la colección mediante el método de **Elemento** , permite a los clientes detectar cuántos elementos se encuentran en la colección mediante la propiedad de **Cuenta** , y permite a menudo que los clientes agregan y que se quita elementos.  
  
-   Una interfaz de enumerador proporciona *acceso serie* *a varios elementos* en una colección, no permite que el cliente detecte cuántos elementos se encuentran en la colección \(hasta el enumerador detiene devoluciones de caso\), y no proporciona ninguna manera de agrega o quita elementos.  
  
 Cada tipo de interfaz desempeña un rol diferente en proporcionar acceso a los elementos de una colección.  
  
## Vea también  
 [Colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)