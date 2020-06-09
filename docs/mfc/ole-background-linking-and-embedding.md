---
title: 'Nociones de OLE: Vincular e incrustar'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
ms.openlocfilehash: 6b6032d2e772728495d4ddb1dbfaa5daf7348b60
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619885"
---
# <a name="ole-background-linking-and-embedding"></a>Nociones de OLE: Vincular e incrustar

El uso del comando pegar en una aplicación contenedora puede crear un componente incrustado, o un elemento incrustado. Los datos de origen de un elemento incrustado se almacenan como parte del documento OLE que lo contiene. De esta manera, un archivo de documento para un documento de procesador de textos puede contener texto y también puede contener mapas de bits, gráficos, fórmulas o cualquier otro tipo de datos.

OLE proporciona otra manera de incorporar datos de otra aplicación: crear un componente vinculado, o un elemento vinculado, o un vínculo. Los pasos para crear un elemento vinculado son similares a los de la creación de un elemento incrustado, con la excepción de que se usa el comando pegar vínculo en lugar del comando pegar. A diferencia de un componente incrustado, un componente vinculado almacena una ruta de acceso a los datos originales, que a menudo se encuentra en un archivo independiente.

Por ejemplo, si está trabajando en un documento de procesador de textos y crea un elemento vinculado a algunas celdas de la hoja de cálculo, los datos del elemento vinculado se almacenan en el documento de hoja de cálculo original. El documento del procesador de textos solo contiene la información que especifica dónde se puede encontrar el elemento, es decir, contiene un vínculo al documento de la hoja de cálculo original. Al hacer doble clic en las celdas, se inicia la aplicación de hoja de cálculo y se carga el documento de la hoja de cálculo original desde donde se almacenó.

Cada elemento OLE, ya sea incrustado o vinculado, tiene un tipo asociado a él en función de la aplicación que lo creó. Por ejemplo, un elemento de Microsoft Paintbrush es un tipo de elemento y un elemento de Microsoft Excel es otro tipo. Sin embargo, algunas aplicaciones pueden crear más de un tipo de elemento. Por ejemplo, Microsoft Excel puede crear elementos de hoja de cálculo, elementos de gráfico y elementos de hoja de macros. El sistema puede identificar de forma única cada uno de estos elementos mediante un identificador de clase o **CLSID**.

## <a name="see-also"></a>Consulte también

[Nociones de OLE](ole-background.md)<br/>
[Nociones de OLE: Contenedores y servidores](ole-background-containers-and-servers.md)<br/>
[Contenedores: Elementos de cliente](containers-client-items.md)<br/>
[Servidores: Elementos de servidor](servers-server-items.md)
