---
title: 'Serialización: Serializar un objeto | Microsoft Docs'
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
ms.openlocfilehash: e05cce1132b180ac8f1350b68d951d776a62315f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381093"
---
# <a name="serialization-serializing-an-object"></a>Serialización: Serializar un objeto

El artículo [serialización: crear una clase Serializable](../mfc/serialization-making-a-serializable-class.md) se muestra cómo hacer que una clase sea serializable. Una vez que una clase serializable, se puede serializar objetos de esa clase a y desde un archivo a través de un [CArchive](../mfc/reference/carchive-class.md) objeto. En este artículo se explica:

- [Es lo que un objeto CArchive](../mfc/what-is-a-carchive-object.md).

- [Dos maneras de crear un objeto CArchive](../mfc/two-ways-to-create-a-carchive-object.md).

- [Cómo usar CArchive <\< y >> operadores](../mfc/using-the-carchive-output-and-input-operators.md).

- [Almacenar y cargar CObjects a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Puede permitir que el marco de crear el contenedor de un documento serializable o bien crear explícitamente la `CArchive` objeto usted mismo. Puede transferir datos entre un archivo y el objeto serializable mediante el <\< y >> operadores para `CArchive` o, en algunos casos, mediante una llamada a la `Serialize` función de un `CObject`-clase derivada.

## <a name="see-also"></a>Vea también

[Serialización](../mfc/serialization-in-mfc.md)

