---
title: Uso de CArchive &lt; &lt; y &gt; &gt; operadores
ms.date: 11/04/2016
f1_keywords:
- CArchive
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 9b4192e79b68388e45eb9837e056bbd881de2933
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259677"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Uso de CArchive &lt; &lt; y &gt; &gt; operadores

`CArchive` Proporciona <\< y >> operadores para escribir y leer los tipos de datos simples, así como `CObject`s hacia y desde un archivo.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Para almacenar un objeto en un archivo a través de un archivo

1. El ejemplo siguiente muestra cómo almacenar un objeto en un archivo a través de un archivo:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Para cargar un objeto de un valor almacenado previamente en un archivo

1. El ejemplo siguiente muestra cómo cargar un objeto de un valor almacenado previamente en un archivo:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Por lo general, almacenar y cargar los datos hacia y desde un archivo a través de un archivo en el `Serialize` funciones de `CObject`-las clases derivadas, que deben haber declarado con la macro DECLARE_SERIALIZE. Una referencia a un `CArchive` objeto se pasa a su `Serialize` función. Se llama a la `IsLoading` función de la `CArchive` objeto para determinar si el `Serialize` se ha llamado la función para cargar datos desde el archivo o almacenar datos en el archivo.

El `Serialize` función de un serializable `CObject`-clase derivada normalmente tiene el formato siguiente:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

La plantilla de código anterior es exactamente el mismo que el Asistente para aplicaciones que se crea para el `Serialize` función del documento (una clase derivada de `CDocument`). Esta plantilla de código le ayuda a escribir código que sea más fácil de revisar, porque el código de almacenamiento y el código de la carga siempre deben ser paralelos, como en el ejemplo siguiente:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

La biblioteca define **< \<** y **>>** operadores para `CArchive` como el primer operando y los siguientes tipos de datos y los tipos de clase como el segundo operando :

||||
|-|-|-|
|`CObject*`|**TAMAÑO** y `CSize`|**float**|
|**WORD**|`CString`|**PUNTO** y `CPoint`|
|`DWORD`|**BYTE**|`RECT` y `CRect`|
|**Double**|**LONG**|`CTime` y `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Almacenar y cargar `CObject`s a través de un archivo requiere una consideración adicional. Para obtener más información, consulte [almacenar y cargar CObjects a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md).

El **CArchive <\<**  y **>>** operadores siempre devuelven una referencia a la `CArchive` objeto, que es el primer operando. Esto le permite encadenar los operadores, como se muestra a continuación:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Vea también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)
