---
title: Uso de una biblioteca de plantillas (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- template libraries
ms.assetid: 5e80ec6e-a61c-41ce-b34b-9a6252c46265
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91a9c10bef285780ded145e33800ebd3db198827
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754804"
---
# <a name="using-a-template-library"></a>Uso de una biblioteca de plantillas

Una plantilla es algo parecido a una macro. Al igual que con una macro, llamar a una plantilla hace que se expanda (con la sustitución de parámetros adecuado) a código que haya escrito. Sin embargo, una plantilla va más allá de esta opción para permitir la creación de nuevas clases basadas en tipos que se pasan como parámetros. Estas nuevas clases implementan la seguridad de tipos de formas de llevar a cabo la operación que se expresa en el código de plantilla.

Bibliotecas de plantillas como ATL se diferencian de bibliotecas de clases de C++ tradicionales en que normalmente se proporcionan únicamente como código fuente (o como código fuente con un poco, compatibilidad con tiempo de ejecución) y no son inherentemente o necesariamente jerárquicas por naturaleza. En lugar de derivar de una clase para obtener la funcionalidad deseada, crear instancias de una clase desde una plantilla.

## <a name="see-also"></a>Vea también

[Introducción a ATL](../atl/introduction-to-atl.md)

