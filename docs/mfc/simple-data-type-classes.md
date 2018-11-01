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
ms.openlocfilehash: 9288ed3104d2cdf4c6938b171166de7cffd32ccf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531667"
---
# <a name="simple-data-type-classes"></a>Clases de tipos de datos simples

Las clases siguientes encapsulan coordenadas, cadenas de caracteres y tiempo de dibujo y la información de fecha, lo que permite cómodo usar sintaxis de C++. Estos objetos se usan ampliamente como parámetros a las funciones miembro de clases de Windows en la biblioteca de clases. Dado que `CPoint`, `CSize`, y `CRect` corresponden a la **punto**, **tamaño**, y **RECT** estructuras, respectivamente, en el SDK de Windows Puede utilizar objetos de estas clases de C++ siempre que utilice estas estructuras del lenguaje C. Las clases proporcionan interfaces útiles a través de sus funciones miembro. `CStringT` proporciona las cadenas de caracteres dinámica muy flexible. `CTime`, `COleDateTime`, `CTimeSpan`, y `COleTimeSpan` representan valores de fecha y hora. Para obtener más información sobre estas clases, vea el artículo [fecha y hora](../atl-mfc-shared/date-and-time.md).

Las clases que comienzan por "`COle`" son las encapsulaciones de tipos de datos proporcionados por OLE. Estos tipos de datos pueden utilizarse en programas de Windows, independientemente de si se utilizan otras características OLE.

[CStringT (clase)](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Contiene las cadenas de caracteres.

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
Contiene valores de fecha y hora absolutos.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Contenedor para el tipo de automatización OLE **fecha**. Representa valores de fecha y hora.

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Contiene valores de fecha y hora relativos.

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Contiene relativa `COleDateTime` valores, como la diferencia entre dos `COleDateTime` valores.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Contiene pares de coordenadas (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Contiene valores emparejados, posiciones relativas o distancia.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Contiene las coordenadas de áreas rectangulares.

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Proporciona la funcionalidad de la lista de imágenes de Windows. Listas de imágenes se usan con los controles de lista y los controles de árbol. También puede usarse para almacenar y archivar un conjunto de mapas de bits mismo tamaño.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Contenedor para el tipo de automatización OLE **VARIANT**. Datos de **VARIANT**s pueden almacenarse en muchos formatos.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Contenedor para el tipo de automatización OLE **moneda**, un tipo aritmético de punto fijo, con 15 dígitos anteriores al separador decimal y 4 dígitos después.

> [!NOTE]
>  `CRect`, `CSize`, y `CPoint` son fáciles de utilizar en aplicaciones de ATL o MFC. Además, `CStringT` proporciona un independientes de MFC `CString`-como clase. Para obtener más información sobre las clases de utilidad compartida, consulte [clases compartidas](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

