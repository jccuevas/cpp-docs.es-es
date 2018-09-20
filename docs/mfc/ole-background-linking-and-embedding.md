---
title: 'Nociones de OLE: Vincular e incrustar | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d4456e5210b2ec1e142c7ddeddd7b0e7fab9f31
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445911"
---
# <a name="ole-background-linking-and-embedding"></a>Nociones de OLE: Vincular e incrustar

Mediante el comando Pegar en una aplicación contenedora puede crear un componente incrustado, o elemento incrustado. Los datos de origen para un elemento incrustado se almacenan como parte del documento OLE que lo contiene. De este modo, un archivo de documento para un documento de procesador de textos puede contener texto y también puede contener los mapas de bits, gráficos, fórmulas o cualquier otro tipo de datos.

OLE proporciona otra manera de incorporar datos desde otra aplicación: crear un componente vinculado o elemento vinculado o un vínculo. Los pasos para crear un elemento vinculado son similares a las de la creación de un elemento incrustado, salvo que use el comando Pegar vínculo en lugar del comando Pegar. A diferencia de un componente incrustado, un componente vinculado almacena una ruta de acceso a los datos originales, que suele ser un archivo independiente.

Por ejemplo, si está trabajando en una palabra documento del procesador y crear un elemento vinculado a algunas celdas de la hoja de cálculo, los datos para el elemento vinculado se almacenan en el documento original de la hoja de cálculo. El documento de procesador de textos contiene sólo la información que especifica dónde puede se encuentra el elemento, es decir, contiene un vínculo al documento de hoja de cálculo original. Cuando hace doble clic en las celdas, se inicia la aplicación de hoja de cálculo y se carga el documento de hoja de cálculo original desde donde se almacena.

Todos los elementos OLE, si incrustado o vinculado, tienen un tipo asociado con él en función de la aplicación que lo creó. Por ejemplo, un elemento de Microsoft Paintbrush es un tipo de elemento y un elemento de Microsoft Excel es otro tipo. Sin embargo, algunas aplicaciones, pueden crear más de un tipo de elemento. Por ejemplo, Microsoft Excel puede crear elementos de la hoja de cálculo, elementos de gráfico y los elementos de la hoja de macros. Cada uno de estos elementos se puede identificar por el sistema mediante un identificador de clase o **CLSID**.

## <a name="see-also"></a>Vea también

[Nociones de OLE](../mfc/ole-background.md)<br/>
[Nociones de OLE: Contenedores y servidores](../mfc/ole-background-containers-and-servers.md)<br/>
[Contenedores: Elementos de cliente](../mfc/containers-client-items.md)<br/>
[Servidores: Elementos de servidor](../mfc/servers-server-items.md)

