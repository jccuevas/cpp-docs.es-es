---
title: 'Nociones de OLE: Vincular e incrustar | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d9b7de075b3c32d130639c60c7fcc389ae37da54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ole-background-linking-and-embedding"></a>Nociones de OLE: Vincular e incrustar
Mediante el comando Pegar en una aplicación contenedora puede crear un componente incrustado, o elemento incrustado. Los datos de origen para un elemento incrustado se almacenan como parte del documento OLE que lo contiene. De este modo, un archivo de documento para un documento de procesador de textos puede contener texto y también puede contener los mapas de bits, gráficos, fórmulas o cualquier otro tipo de datos.  
  
 OLE proporciona otra forma de incorporar datos de otra aplicación: crear un componente vinculado o elemento vinculado o un vínculo. Los pasos para crear un elemento vinculado son similares a las de creación de un elemento incrustado, salvo que use el comando Pegar vínculo en lugar del comando Pegar. A diferencia de un componente incrustado, un componente vinculado almacena una ruta de acceso a los datos originales, que suele ser en un archivo independiente.  
  
 Por ejemplo, si está trabajando en una palabra documento del procesador y crear un elemento vinculado a algunas celdas de la hoja de cálculo, los datos para el elemento vinculado se almacenan en el documento de hoja de cálculo original. El documento de procesador de textos contiene sólo la información que se especifica que el elemento puede encontrarse, es decir, contiene un vínculo en el documento de hoja de cálculo original. Cuando hace doble clic en las celdas, se inicia la aplicación de hoja de cálculo y se carga el documento de hoja de cálculo original desde donde se almacenó.  
  
 Todos los elementos OLE, si incrustados o vinculados, tienen un tipo asociado a él basándose en la aplicación que lo creó. Por ejemplo, un elemento de Microsoft Paintbrush es un tipo de elemento y un elemento de Microsoft Excel es otro tipo. Sin embargo, algunas aplicaciones, pueden crear más de un tipo de elemento. Por ejemplo, Microsoft Excel puede crear elementos de hoja de cálculo, los elementos del gráfico y los elementos de hoja de macros. Cada uno de estos elementos puede identificarse de forma exclusiva el sistema mediante un identificador de clase o **CLSID**.  
  
## <a name="see-also"></a>Vea también  
 [Nociones de OLE](../mfc/ole-background.md)   
 [Nociones de OLE: Contenedores y servidores](../mfc/ole-background-containers-and-servers.md)   
 [Contenedores: Elementos de cliente](../mfc/containers-client-items.md)   
 [Servidores: Elementos de servidor](../mfc/servers-server-items.md)

