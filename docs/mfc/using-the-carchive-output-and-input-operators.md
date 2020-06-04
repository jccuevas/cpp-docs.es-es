---
title: Uso de &lt; &lt; CArchive y &gt; &gt; Operadores
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 91ea565867cc0cb3b27ad9d5597037b637cb6544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368958"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Uso de &lt; &lt; CArchive y &gt; &gt; Operadores

`CArchive`proporciona \< <y operadores >> para escribir `CObject`y leer tipos de datos simples, así como s a y desde un archivo.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Para almacenar un objeto en un archivo a través de un archivo

1. En el ejemplo siguiente se muestra cómo almacenar un objeto en un archivo a través de un archivo:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Para cargar un objeto desde un valor almacenado previamente en un archivo

1. En el ejemplo siguiente se muestra cómo cargar un objeto desde un valor almacenado anteriormente en un archivo:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Normalmente, se almacenan y cargan datos desde `Serialize` y `CObject`hacia un archivo a través de un archivo en las funciones de las clases derivadas, que debe haber declarado con la macro DECLARE_SERIALIZE. Se pasa `CArchive` una referencia a `Serialize` un objeto a la función. Llame a `IsLoading` la `CArchive` función del `Serialize` objeto para determinar si se ha llamado a la función para cargar datos desde el archivo o almacenar datos en el archivo.

La `Serialize` función de `CObject`una clase derivada serializable normalmente tiene la siguiente forma:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

La plantilla de código anterior es exactamente la `Serialize` misma que la que AppWizard `CDocument`crea para la función del documento (una clase derivada de ). Esta plantilla de código le ayuda a escribir código que es más fácil de revisar, porque el código de almacenamiento y el código de carga siempre deben ser paralelos, como en el ejemplo siguiente:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

La biblioteca ** < ** **>>** define `CArchive` y los operadores para como el primer operando y los siguientes tipos de datos y tipos de clase como el segundo operando:

||||
|-|-|-|
|`CObject*`|**TALLA** Y`CSize`|**Flotador**|
|**Palabra**|`CString`|**PUNTO** y`CPoint`|
|`DWORD`|**Byte**|`RECT` y `CRect`|
|**Double**|**Largo**|`CTime` y `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> Almacenar y `CObject`cargar s a través de un archivo requiere una consideración adicional. Para obtener más información, consulte Almacenamiento y carga de [CObjects a través](../mfc/storing-and-loading-cobjects-via-an-archive.md)de un archivo .

El **CArchive \< ** **>>** <y los operadores siempre devuelven una referencia al `CArchive` objeto, que es el primer operando. Esto le permite encadenar los operadores, como se ilustra a continuación:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Consulte también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)
