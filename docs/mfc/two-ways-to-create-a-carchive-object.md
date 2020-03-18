---
title: Dos maneras de crear un objeto CArchive
ms.date: 11/04/2016
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
ms.openlocfilehash: 38642906b0973730149ed0de5381519f06d69fe5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442028"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dos maneras de crear un objeto CArchive

Hay dos maneras de crear un objeto `CArchive`:

- [Creación implícita de un objeto CArchive a través del marco](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Creación explícita de un objeto CArchive](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Creación implícita de un objeto CArchive a través del marco

La manera más común y más sencilla es dejar que el marco de trabajo cree un `CArchive` objeto para el documento en nombre de los comandos guardar, guardar como y abrir en el menú archivo.

Este es el marco de trabajo cuando el usuario de la aplicación emite el comando Guardar como en el menú Archivo:

1. Presenta el cuadro de diálogo **Guardar como** y obtiene el nombre de archivo del usuario.

1. Abre el archivo denominado por el usuario como un objeto de `CFile`.

1. Crea un objeto `CArchive` que apunta a este objeto `CFile`. Al crear el objeto `CArchive`, el marco de trabajo establece el modo en "Store" (escritura, serialización), en lugar de "Load" (lectura, deserialización).

1. Llama a la función `Serialize` definida en la clase derivada de `CDocument`, pasándole una referencia al objeto `CArchive`.

La función `Serialize` del documento escribe los datos en el objeto `CArchive`, tal y como se explica en breve. Al volver de la función `Serialize`, el marco de trabajo destruye el objeto `CArchive` y, a continuación, el objeto `CFile`.

Por lo tanto, si permite que el marco de trabajo cree el objeto de `CArchive` para el documento, lo único que tiene que hacer es implementar la función de `Serialize` del documento que escribe y lee en el archivo. También tiene que implementar `Serialize` para cualquier objeto derivado de `CObject`que la función `Serialize` del documento, a su vez, se serializa de forma directa o indirecta.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a>Creación explícita de un objeto CArchive

Además de serializar un documento a través del marco de trabajo, hay otras ocasiones en las que es posible que necesite un objeto `CArchive`. Por ejemplo, es posible que desee serializar datos hacia y desde el portapapeles, representado por un objeto `CSharedFile`. O bien, puede que desee usar una interfaz de usuario para guardar un archivo diferente del proporcionado por el marco. En este caso, puede crear explícitamente un objeto de `CArchive`. Esto se hace de la misma manera que el marco de trabajo, mediante el procedimiento siguiente.

#### <a name="to-explicitly-create-a-carchive-object"></a>Para crear explícitamente un objeto CArchive

1. Construya un objeto de `CFile` o un objeto derivado de `CFile`.

1. Pase el objeto `CFile` al constructor de `CArchive`, como se muestra en el ejemplo siguiente:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   El segundo argumento del constructor `CArchive` es un valor enumerado que especifica si el archivo se utilizará para almacenar o cargar datos en el archivo o desde él. La función `Serialize` de un objeto comprueba este estado mediante una llamada a la función `IsStoring` para el objeto de almacenamiento.

Cuando haya terminado de almacenar o cargar datos en el objeto `CArchive`, ciérrelo. Aunque los objetos `CArchive` (y `CFile`) cerrarán automáticamente el archivo (y el archivo), se recomienda hacerlo explícitamente, ya que facilita la recuperación de los errores. Para obtener más información sobre el control de errores, vea el artículo [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Para cerrar el objeto CArchive

1. En el ejemplo siguiente se muestra cómo cerrar el objeto `CArchive`:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Consulte también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)
