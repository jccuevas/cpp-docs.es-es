---
title: "Dos maneras de crear un objeto CArchive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive (clase), cerrar objetos CArchive"
  - "CArchive (clase), constructor"
  - "CArchive (objetos)"
  - "CArchive (objetos), cerrar"
  - "almacenamiento de datos [C++], CArchive (clase)"
  - "E/S [MFC], crear objetos CArchive"
  - "serialización [C++], CArchive (clase)"
  - "almacenamiento [C++], CArchive (clase)"
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dos maneras de crear un objeto CArchive
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay dos maneras de crear un objeto de `CArchive` :  
  
-   [Creación implícita de un objeto CArchive mediante el marco](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [Creación explícita de un objeto CArchive](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> Creación implícita de un objeto CArchive mediante el marco  
 El más común, y más fácil, es dejar el marco crear un objeto de `CArchive` para el documento en nombre de Guardar, de Guardar como, y los comandos abierto en el menú archivo.  
  
 Esto es lo que hace el marco cuando el usuario de los problemas de la aplicación el Guardar como comando de menú archivo:  
  
1.  Muestra el cuadro de diálogo de **Guardar como** y obtiene el nombre de archivo de usuario.  
  
2.  Abra el archivo denominado por el usuario como objeto de `CFile` .  
  
3.  Crea un objeto de `CArchive` que elija este `CFile` el objeto.  Para crear el objeto de `CArchive` , el marco establece el modo “para almacenar” \(la escritura, serializa\), en lugar de “carga” \(lectura, deserializa\).  
  
4.  Llama a la función de `Serialize` definida en **CDocument**\- clase derivada, pasándole una referencia al objeto de `CArchive` .  
  
 La función de `Serialize` de documento escribir datos al objeto de `CArchive` , como se explica anteriormente.  Al volver de la función de `Serialize` , el marco destruye el objeto de `CArchive` y el objeto de `CFile` .  
  
 Así, si deja el marco crear el objeto de `CArchive` para el documento, lo único que debe hacer es implementar la función de `Serialize` de documento que escribe y lee al archivo.  También tiene que implementar `Serialize` para cualquier `CObject`\- objetos derivados que la función de `Serialize` de documento a su vez serializa directa o indirectamente.  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a> Creación explícita de un objeto CArchive  
 Además de serializar un documento mediante el marco, hay otras ocasiones puede necesitar un objeto de `CArchive` .  Por ejemplo, puede que desee serializar datos a y desde el portapapeles, representado por un objeto de `CSharedFile` .  O bien, se puede utilizar una interfaz de usuario para guardar un archivo diferente del que está proporcionada por el marco de trabajo.  En este caso, puede crear explícitamente un objeto de `CArchive` .  Esto se hace de la misma manera que lo hace el marco, mediante el procedimiento siguiente.  
  
#### Para crear explícitamente un objeto CArchive  
  
1.  Crea un objeto de `CFile` o un objeto derivado de `CFile`.  
  
2.  Pase el objeto de `CFile` el constructor para `CArchive`, como se muestra en el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/CPP/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     El segundo argumento al constructor de `CArchive` es un valor enumerado que especifica si el archivo se utilizará para almacenar o cargar datos a o desde un archivo.  La función de `Serialize` de un objeto comprueba este estado llamando a la función de `IsStoring` para el objeto de archivo.  
  
 Cuando es almacenar finalizado o cargar datos a o desde el objeto de `CArchive` , ciérrela.  Aunque cierren los objetos de `CArchive` \(y `CFile`\) automáticamente el archivo \(y archivo\), es recomendable a explícitamente hacerlo ya que crea la recuperación de errores más fácil.  Para obtener más información sobre control de errores, vea el artículo [Excepciones: Detectando y eliminar Excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
#### Para cerrar el objeto CArchive  
  
1.  El ejemplo siguiente se muestra cómo cerrar el objeto de `CArchive` :  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/CPP/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## Vea también  
 [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)