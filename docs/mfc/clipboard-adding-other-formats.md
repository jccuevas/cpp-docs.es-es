---
title: "Portapapeles: Agregar otros formatos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Portapapeles, formatos"
  - "formatos de datos personalizados del Portapapeles"
  - "formatos personalizados"
  - "formatos personalizados, poner en el Portapapeles"
  - "formatos [C++], Portapapeles"
  - "registrar formatos de datos personalizados del Portapapeles"
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Portapapeles: Agregar otros formatos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo expandir la lista de formatos admitidos, especialmente para compatibilidad OLE.  El tema [Portapapeles: Copiando y pegando datos](../mfc/clipboard-copying-and-pasting-data.md) describe la implementación mínima necesaria para admitir copiar y pegar desde el portapapeles.  Si es todo implementa, los únicos formatos incluidos en el portapapeles es `CF_METAFILEPICT`, **CF\_EMBEDSOURCE**, **CF\_OBJECTDESCRIPTOR**y, posiblemente `CF_LINKSOURCE`.  La mayoría de las aplicaciones necesitarán más formatos en el portapapeles que estos tres.  
  
##  <a name="_core_registering_custom_formats"></a> Registrar formatos personalizados de  
 Para crear dispone de formatos de custom, siga el mismo procedimiento que utilizaría el registro cualquier formato de Portapapeles personalizado: pase el nombre de formato a la función de **RegisterClipboardFormat** y utilice el valor devuelto como el identificador de formato  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a> Colocar formatos en el portapapeles  
 Para agregar más formatos similares a colocar en el portapapeles, debe reemplazar la función de `OnGetClipboardData` en la clase que se derivó de `COleClientItem` o de `COleServerItem` \(dependiendo de si los datos se copiará es nativo\).  En esta función, debe utilizar el procedimiento siguiente.  
  
#### Para colocar formatos en el portapapeles  
  
1.  Crear un objeto `COleDataSource`.  
  
2.  Pase este origen de datos a una función que agregue los formatos de datos nativos a la lista de formatos admitidos llamando a `COleDataSource::CacheGlobalData`.  
  
3.  Agregue los formatos estándar llamando a `COleDataSource::CacheGlobalData` para cada formato estándar que desee.  
  
 Esta técnica se utiliza en el programa de ejemplo OLE [HIERSVR](../top/visual-cpp-samples.md) de MFC \(examine la función miembro de `OnGetClipboardData` de la clase de **CServerItem** \).  La única diferencia en este ejemplo es que el paso tres no se implementa porque HIERSVR no admite ningún otro formato estándar.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Objetos de datos de OLE y orígenes de datos y transferencia de datos uniforme](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [Arrastrar y colocar de OLE](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## Vea también  
 [Portapapeles: Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)