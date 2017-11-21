---
title: "Serialización: Serializar un objeto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1339f7ab6b226da9f233e523171e318209e99ee4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="serialization-serializing-an-object"></a>Serialización: Serializar un objeto
El artículo [serialización: crear una clase Serializable](../mfc/serialization-making-a-serializable-class.md) muestra cómo hacer que una clase serializable. Una vez que tenga una clase serializable, es posible serializar objetos de esa clase a y desde un archivo a través de un [CArchive](../mfc/reference/carchive-class.md) objeto. Este artículo se explica:  
  
-   [¿Qué un objeto CArchive es](../mfc/what-is-a-carchive-object.md).  
  
-   [Dos maneras de crear un objeto CArchive](../mfc/two-ways-to-create-a-carchive-object.md).  
  
-   [Cómo usar el CArchive <\< y >> operadores](../mfc/using-the-carchive-output-and-input-operators.md).  
  
-   [Almacenar y cargar CObjects a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md).  
  
 Puede dejar que el marco de trabajo cree el archivo de un documento serializable o bien crear explícitamente la `CArchive` objeto usted mismo. Puede transferir datos entre un archivo y el objeto serializable mediante el <\< y >> operadores para `CArchive` o, en algunos casos, mediante una llamada a la `Serialize` función de un `CObject`-clase derivada.  
  
## <a name="see-also"></a>Vea también  
 [Serialización](../mfc/serialization-in-mfc.md)

