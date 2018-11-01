---
title: Dos maneras de crear un objeto CArchive? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 630cdd1614aa19ec3a5a654d7dc4bfe7336ce027
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080590"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dos maneras de crear un objeto CArchive

Hay dos maneras de crear un `CArchive` objeto:

- [Creación implícita de un objeto CArchive mediante el marco de trabajo](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [¿Creación explícita de un objeto CArchive?](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> Creación implícita de un objeto CArchive mediante el marco de trabajo

Es la manera más común y más fácil permitir que el marco de trabajo de creación de un `CArchive` objeto para el documento en nombre de la guardar, guardar como y comandos de apertura en el menú archivo.

Esto es lo que hace el marco de trabajo cuando el usuario de la aplicación emite el comando Guardar como en el menú archivo:

1. Presenta el **Guardar como** cuadro de diálogo y obtiene el nombre de archivo del usuario.

1. Abre el archivo especificado por el usuario como un `CFile` objeto.

1. Crea un `CArchive` objeto que haga referencia a este `CFile` objeto. En la creación de la `CArchive` de objeto, el marco de trabajo establece el modo de "store" (escribir, serializar), en lugar de "carga" (leer, deserializar).

1. Las llamadas del `Serialize` función definida en su `CDocument`-clase derivada, se pasa una referencia a la `CArchive` objeto.

El documento `Serialize` función, a continuación, escribe datos en el `CArchive` de objeto, como se explica en breve. Vuelve desde su `Serialize` función, el marco de trabajo destruye el `CArchive` objeto y, a continuación, el `CFile` objeto.

Por lo tanto, si permite que el marco de trabajo crear los `CArchive` de objeto para el documento, lo único que debe hacer es implementar el documento `Serialize` función que se escribe y lee hacia y desde el archivo. También debe implementar `Serialize` para cualquier `CObject`-objetos derivados que el documento `Serialize` función serializa a su vez directa o indirectamente.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a> ¿Creación explícita de un objeto CArchive?

Además de serializar un documento mediante el marco de trabajo, existen otras ocasiones cuando es posible que necesite un `CArchive` objeto. Por ejemplo, desea serializar datos hacia y desde el Portapapeles, representado por un `CSharedFile` objeto. O bien, si desea usar una interfaz de usuario para guardar un archivo que es diferente del que ofrece el marco de trabajo. En este caso, puede crear explícitamente un `CArchive` objeto. Para ello la misma manera que hace el marco de trabajo, utilizando el procedimiento siguiente.

#### <a name="to-explicitly-create-a-carchive-object"></a>¿Para crear explícitamente un objeto CArchive?

1. Construir un `CFile` objeto o un objeto derivado de `CFile`.

1. Pase el `CFile` objeto al constructor para `CArchive`, como se muestra en el ejemplo siguiente:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   El segundo argumento para el `CArchive` constructor es un valor enumerado que especifica si el archivo se usará para almacenar o cargar datos a o desde el archivo. El `Serialize` función de un objeto comprueba este estado mediante una llamada a la `IsStoring` función del objeto de almacenamiento.

Cuando haya terminado de almacenar o cargar datos desde o hacia el `CArchive` de objetos, ciérrelo. Aunque el `CArchive` (y `CFile`) los objetos cerrará automáticamente el archivo (y el archivo), es recomendable hacerlo explícitamente ya que facilita la recuperación de errores. Para obtener más información sobre el control de errores, vea el artículo [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Para cerrar el objeto CArchive

1. El ejemplo siguiente muestra cómo cerrar la `CArchive` objeto:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Vea también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

