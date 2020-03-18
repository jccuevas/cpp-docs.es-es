---
title: Usar los operadores &lt; de &lt;CArchive y &gt;&gt;
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 8e175f35f2218341c69571c818711596180df4a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442176"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Usar los operadores &lt; de &lt;CArchive y &gt;&gt;

`CArchive` proporciona < operadores\< y > > para escribir y leer tipos de datos simples, así como `CObject`s hacia y desde un archivo.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Para almacenar un objeto en un archivo a través de un archivo

1. En el ejemplo siguiente se muestra cómo almacenar un objeto en un archivo a través de un archivo:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Para cargar un objeto a partir de un valor almacenado previamente en un archivo

1. En el ejemplo siguiente se muestra cómo cargar un objeto a partir de un valor almacenado previamente en un archivo:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Normalmente, los datos se almacenan y se cargan desde y hacia un archivo a través de un archivo en las funciones de `Serialize` de clases derivadas de `CObject`, que se deben haber declarado con la macro DECLARE_SERIALIZE. Una referencia a un objeto `CArchive` se pasa a la función `Serialize`. Llame a la función `IsLoading` del objeto `CArchive` para determinar si se ha llamado a la función `Serialize` para cargar los datos del archivo o almacenar los datos en el archivo.

Normalmente, la función `Serialize` de una clase serializable `CObject`derivada tiene el formato siguiente:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

La plantilla de código anterior es exactamente la misma que la que crea AppWizard para la función `Serialize` del documento (una clase derivada de `CDocument`). Esta plantilla de código le ayuda a escribir código que es más fácil de revisar, ya que el código de almacenamiento y el código de carga siempre deben ser paralelos, como en el ejemplo siguiente:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

La biblioteca define **<operadores \<** y **>>** para `CArchive` como el primer operando y los siguientes tipos de datos y tipos de clase como segundo operando:

||||
|-|-|-|
|`CObject*`|**Tamaño** y `CSize`|**float**|
|**WORD**|`CString`|**Punto** y `CPoint`|
|`DWORD`|**BYTE**|`RECT` y `CRect`|
|**Doble**|**LONG**|`CTime` y `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Almacenar y cargar `CObject`s a través de un archivo requiere una consideración adicional. Para obtener más información, vea [almacenar y cargar CObjects a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Los operadores **<\<** y **>>** de CArchive siempre devuelven una referencia al objeto `CArchive`, que es el primer operando. Esto le permite encadenar los operadores, como se muestra a continuación:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Consulte también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)
