---
title: Clases de tipos de datos simples | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54d7f200ee35489f37256023d28bdd3260bf48ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="simple-data-type-classes"></a>Clases de tipos de datos simples
Las clases siguientes encapsulan dibujo coordenadas, cadenas de caracteres y la hora y la información de fecha, lo que permite cómodo usar sintaxis de C++. Estos objetos se utilizan ampliamente como parámetros a las funciones miembro de clases de Windows en la biblioteca de clases. Dado que `CPoint`, `CSize`, y `CRect` corresponden a la **punto**, **tamaño**, y `RECT` las estructuras, respectivamente, en el SDK de Windows, puede utilizar objetos de estos Siempre que pueda utilizar estas estructuras del lenguaje C, las clases C++. Las clases proporcionan interfaces útiles a través de sus funciones miembro. `CStringT` proporciona las cadenas de caracteres dinámica muy flexible. `CTime`, `COleDateTime`, `CTimeSpan`, y **COleTimeSpan** representan valores de fecha y hora. Para obtener más información sobre estas clases, vea el artículo [fecha y hora](../atl-mfc-shared/date-and-time.md).  
  
 Las clases que comienzan por "**COle**" son encapsulaciones de tipos de datos proporcionados por OLE. Estos tipos de datos se pueden utilizar en programas de Windows, independientemente de si se utilizan otras características OLE.  
  
 [CStringT (clase)](../atl-mfc-shared/reference/cstringt-class.md)  
 Contiene las cadenas de caracteres.  
  
 [CTime](../atl-mfc-shared/reference/ctime-class.md)  
 Contiene valores de fecha y hora absolutos.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Contenedor para el tipo de automatización OLE **fecha**. Representa valores de fecha y hora.  
  
 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)  
 Contiene valores de fecha y hora relativos.  
  
 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)  
 Contiene relativa `COleDateTime` valores, como la diferencia entre dos `COleDateTime` valores.  
  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Contiene pares de coordenadas (x, y).  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Contiene valores emparejados, posiciones relativas o distancia.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Contiene coordenadas de áreas rectangulares.  
  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 Proporciona la funcionalidad de la lista de imágenes de Windows. Se utilizan listas de imágenes con controles de lista y controles de árbol. Pueden usarse para almacenar y archivar un conjunto de mapas de bits mismo tamaño.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Contenedor para el tipo de automatización OLE **VARIANT**. Datos de **VARIANT**s pueden almacenarse en muchos formatos.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 Contenedor para el tipo de automatización OLE **moneda**, un tipo aritmético punto fijo, con 15 dígitos que hay delante del separador decimal y 4 dígitos después.  
  
> [!NOTE]
>  `CRect`, `CSize`, y `CPoint` están para su uso en aplicaciones de ATL o MFC. Además, `CStringT` proporciona un independientes de MFC `CString`-como clase. Para obtener más información sobre las clases de utilidad compartida, consulte [clases compartidas](../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

