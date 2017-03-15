---
title: "Nociones de OLE: Vincular e incrustar | Microsoft Docs"
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
  - "objetos incrustados [C++]"
  - "tipos de elemento"
  - "tipos de elemento, definición"
  - "elementos vinculados (OLE) [C++]"
  - "elementos incrustados OLE"
  - "elementos OLE, tipos"
  - "OLE, elementos vinculados"
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Nociones de OLE: Vincular e incrustar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Mediante el comando pegar en una aplicación contenedora puede crear un componente incrustado, o el elemento incrustado.  Los datos de origen para un elemento incrustado se almacenan como parte del documento OLE que lo contiene.  De esta manera, un archivo de documento para un documento de procesador de textos puede contener texto y también puede contener mapas de bits, dibujos, fórmulas, o cualquier otro tipo de datos.  
  
 OLE proporciona otra manera de especificar datos de otra aplicación: crear un componente vinculado, o elemento vinculado, o un vínculo.  Los pasos para crear un elemento vinculado son similares a los de crear un elemento incrustado, salvo que utilice el comando de pegar vínculos en lugar del comando pegar.  A diferencia de un componente incrustado, un componente vinculado almacena una ruta de acceso a datos original, que está en un archivo independiente.  
  
 Por ejemplo, si está trabajando en un documento de procesador de textos y crea un elemento vinculado a algunas celdas de hoja de cálculo, los datos para el elemento vinculado se almacena en el documento de la hoja de cálculo original.  El documento de procesador de textos sólo contiene información que especifica donde el elemento se encuentra, es decir, contiene un vínculo al documento de la hoja de cálculo original.  Cuando se hace doble clic en las celdas, se inicia la aplicación de la hoja de cálculo y el documento de la hoja de cálculo original se carga de donde se almacenó.  
  
 Cada elemento OLE, es incrustado o vinculado, tiene un tipo asociado al basándose en la aplicación que lo creó.  Por ejemplo, un elemento de Microsoft Paintbrush es un tipo de elemento, y un elemento de Microsoft Excel es otro tipo.  Algunas aplicaciones, sin embargo, pueden crear más de un tipo de elemento.  Por ejemplo, Microsoft Excel puede crear elementos de la hoja de cálculo, elementos de gráfico, y elementos de hoja de macros.  Cada uno de estos elementos se puede identificar el sistema mediante un identificador de clase o **CLSID**.  
  
## Vea también  
 [Nociones de OLE](../mfc/ole-background.md)   
 [Nociones de OLE: Contenedores y servidores](../mfc/ole-background-containers-and-servers.md)   
 [Contenedores: Elementos de cliente](../mfc/containers-client-items.md)   
 [Servidores: Elementos de servidor](../mfc/servers-server-items.md)