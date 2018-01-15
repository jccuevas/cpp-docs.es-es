---
title: Dos maneras de crear un objeto CArchive? | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CArchive
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b1db549544d421600ed6dae1a8a987006c2ab6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dos maneras de crear un objeto CArchive
Hay dos maneras de crear un `CArchive` objeto:  
  
-   [Creación implícita de un objeto CArchive mediante el marco de trabajo](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [¿Creación explícita de un objeto CArchive?](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Creación implícita de un objeto CArchive mediante el marco de trabajo  
 La manera más común y más sencilla, es dejar que el marco de trabajo cree una `CArchive` objeto para el documento en nombre del guardar, guardar como y comandos de apertura en el menú archivo.  
  
 Esto es lo que hace el marco de trabajo cuando el usuario de la aplicación emite el comando Guardar como en el menú archivo:  
  
1.  Presenta el **Guardar como** cuadro de diálogo y obtiene el nombre de archivo del usuario.  
  
2.  Abre el archivo especificado por el usuario como un `CFile` objeto.  
  
3.  Crea un `CArchive` objeto que apunta a este `CFile` objeto. En la creación de la `CArchive` del objeto, el marco de trabajo establece el modo de "store" (escribir, serializar), en lugar de "carga" (lectura, deserializar).  
  
4.  Llamadas a la `Serialize` función definida en su **CDocument**-clase derivada, pasando una referencia a la `CArchive` objeto.  
  
 El documento `Serialize` función, a continuación, escribe datos en el `CArchive` de objeto, como se explica en breve. Tras la devolución de su `Serialize` función, el marco de trabajo destruye el `CArchive` objeto y, a continuación, el `CFile` objeto.  
  
 Por lo tanto, si permite que el marco de trabajo cree el `CArchive` de objeto para el documento, lo único que debe hacer es implementar el documento `Serialize` función a la que se escribe y lee hacia y desde el archivo. También tiene que implementar `Serialize` para cualquier `CObject`-objetos derivados que el documento `Serialize` función serializa a su vez directa o indirectamente.  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a>¿Creación explícita de un objeto CArchive?  
 Además de serializar un documento mediante el marco de trabajo, hay otras ocasiones cuando necesite una `CArchive` objeto. Por ejemplo, desea serializar datos desde y hacia el Portapapeles, representado por un `CSharedFile` objeto. O bien, puede que desee utilizar una interfaz de usuario para guardar un archivo que es diferente de la que ofrece el marco de trabajo. En este caso, puede crear explícitamente un `CArchive` objeto. Para ello la misma manera que el marco de trabajo, utilizando el procedimiento siguiente.  
  
#### <a name="to-explicitly-create-a-carchive-object"></a>¿Para crear explícitamente un objeto CArchive?  
  
1.  Construir un `CFile` objeto o un objeto derivado de `CFile`.  
  
2.  Pasar el `CFile` objeto al constructor de `CArchive`, como se muestra en el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     El segundo argumento para el `CArchive` constructor es un valor enumerado que especifica si el archivo se utilizará para almacenar o cargar datos a o desde el archivo. El `Serialize` función de un objeto comprueba este estado mediante una llamada a la `IsStoring` función para el objeto de archivo.  
  
 Cuando haya terminado de almacenar o cargar datos desde o hacia el `CArchive` de objetos, ciérrelo. Aunque la `CArchive` (y `CFile`) objetos cerrará automáticamente el archivo (y el archivo), es recomendable hacerlo explícitamente desde que facilita la recuperación de errores. Para obtener más información sobre el control de errores, vea el artículo [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
#### <a name="to-close-the-carchive-object"></a>¿Para cerrar el objeto CArchive?  
  
1.  En el ejemplo siguiente se muestra cómo cerrar la `CArchive` objeto:  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

