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
ms.openlocfilehash: 71592584d4ecdd3169ad894861a97fa668c04ee8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370957"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dos maneras de crear un objeto CArchive

Hay dos formas de `CArchive` crear un objeto:

- [Creación implícita de un objeto CArchive a través del marco de trabajo](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Creación explícita de un objeto CArchive](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Creación implícita de un objeto CArchive a través del marco de trabajo

La forma más común y sencilla es permitir `CArchive` que el marco de trabajo cree un objeto para el documento en nombre de los comandos Guardar, Guardar como y Abrir del menú Archivo.

Esto es lo que hace el marco de trabajo cuando el usuario de la aplicación emite el comando Guardar como del menú Archivo:

1. Presenta el cuadro de diálogo **Guardar como** y obtiene el nombre de archivo del usuario.

1. Abre el archivo nombrado por `CFile` el usuario como un objeto.

1. Crea `CArchive` un objeto que `CFile` apunta a este objeto. Al crear `CArchive` el objeto, el marco de trabajo establece el modo en "store" (escribir, serializar), en lugar de "load" (leer, deserializar).

1. Llama `Serialize` a la `CDocument`función definida en la clase `CArchive` derivada, pasándole una referencia al objeto.

A continuación, `Serialize` la función del `CArchive` documento escribe datos en el objeto, como se explica en breve. Al volver `Serialize` de la función, `CArchive` el marco `CFile` de trabajo destruye el objeto y, a continuación, el objeto.

Por lo tanto, si `CArchive` permite que el marco de trabajo cree el `Serialize` objeto para el documento, todo lo que tiene que hacer es implementar la función del documento que escribe y lee en y desde el archivo. También tiene que `Serialize` implementar `CObject`para cualquier objeto derivado `Serialize` que la función del documento a su vez serializa directa o indirectamente.

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a>Creación explícita de un objeto CArchive

Además de serializar un documento a través del `CArchive` marco de trabajo, hay otras ocasiones en las que es posible que necesite un objeto. Por ejemplo, es posible que desee serializar datos `CSharedFile` hacia y desde el Portapapeles, representado por un objeto. O bien, es posible que desee utilizar una interfaz de usuario para guardar un archivo que es diferente del que ofrece el marco de trabajo. En este caso, puede crear `CArchive` explícitamente un objeto. Esto se hace de la misma manera que lo hace el marco de trabajo, mediante el siguiente procedimiento.

#### <a name="to-explicitly-create-a-carchive-object"></a>Para crear explícitamente un CArchive objeto

1. Construir `CFile` un objeto o un `CFile`objeto derivado de .

1. Pase `CFile` el objeto al `CArchive`constructor para , como se muestra en el ejemplo siguiente:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   El segundo argumento `CArchive` para el constructor es un valor enumerado que especifica si el archivo se usará para almacenar o cargar datos desde o hacia el archivo. La `Serialize` función de un objeto comprueba `IsStoring` este estado llamando a la función para el objeto de archivado.

Cuando haya terminado de almacenar o cargar `CArchive` datos desde o hacia el objeto, ciérrelos. Aunque `CArchive` los `CFile`objetos (y ) cerrarán automáticamente el archivo (y el archivo), es recomendable hacerlo explícitamente, ya que facilita la recuperación de errores. Para obtener más información sobre el control de errores, vea el artículo [Excepciones: captura y eliminación](../mfc/exceptions-catching-and-deleting-exceptions.md)de excepciones .

#### <a name="to-close-the-carchive-object"></a>Para cerrar el objeto CArchive

1. En el ejemplo siguiente se `CArchive` muestra cómo cerrar el objeto:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Consulte también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)
