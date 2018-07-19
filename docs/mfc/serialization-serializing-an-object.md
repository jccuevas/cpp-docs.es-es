---
title: 'Serialización: Serializar un objeto | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3439857f14f4c4fa78aa2df3e3da8e5c8941938d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379663"
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

