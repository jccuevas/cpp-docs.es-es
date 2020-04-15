---
title: Clases de tipos de datos simples
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: d4038334e35b734370a437d35519498b96c00770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365397"
---
# <a name="simple-data-type-classes"></a>Clases de tipos de datos simples

Las clases siguientes encapsulan las coordenadas de dibujo, las cadenas de caracteres y la información de fecha y hora, lo que permite un uso conveniente de la sintaxis de C++. Estos objetos se utilizan ampliamente como parámetros para las funciones miembro de las clases de Windows en la biblioteca de clases. Dado `CPoint` `CSize`que `CRect` , , y corresponden a las estructuras **POINT**, **SIZE**y **RECT,** respectivamente, en el Windows SDK, puede usar objetos de estas clases C++ siempre que pueda usar estas estructuras de lenguaje C. Las clases proporcionan interfaces útiles a través de sus funciones miembro. `CStringT`proporciona cadenas de caracteres dinámicos muy flexibles. `CTime`, `COleDateTime` `CTimeSpan`, `COleTimeSpan` , y representan valores de fecha y hora. Para obtener más información acerca de estas clases, vea el artículo [Fecha y hora](../atl-mfc-shared/date-and-time.md).

Las clases que`COle`comienzan con " " son encapsulaciones de tipos de datos proporcionados por OLE. Estos tipos de datos se pueden usar en programas de Windows independientemente de si se usan otras características OLE.

[Clase CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Contiene cadenas de caracteres.

[Ctime](../atl-mfc-shared/reference/ctime-class.md)<br/>
Contiene valores absolutos de fecha y hora.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Contenedor para el tipo de automatización OLE **DATE**. Representa los valores de fecha y hora.

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Contiene valores relativos de fecha y hora.

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Contiene valores `COleDateTime` relativos, como la `COleDateTime` diferencia entre dos valores.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Mantiene los pares de coordenadas (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Mantiene la distancia, las posiciones relativas o los valores emparejados.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Mantiene las coordenadas de las áreas rectangulares.

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Proporciona la funcionalidad de la lista de imágenes de Windows. Las listas de imágenes se utilizan con controles de lista y controles de árbol. También se pueden utilizar para almacenar y archivar un conjunto de mapas de bits del mismo tamaño.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Contenedor para el tipo de automatización OLE **VARIANT**. Los datos de **VARIANT**s se pueden almacenar en muchos formatos.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Wrapper para el tipo de automatización OLE **CURRENCY**, un tipo aritmético de punto fijo, con 15 dígitos antes del punto decimal y 4 dígitos después.

> [!NOTE]
> `CRect`, `CSize`, `CPoint` y se pueden usar en aplicaciones ATL o MFC. Además, `CStringT` proporciona una `CString`clase similar independiente de MFC. Para obtener más información sobre las clases de utilidad compartidas, vea [Clases compartidas](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Consulte también

[Información general de clases](../mfc/class-library-overview.md)
