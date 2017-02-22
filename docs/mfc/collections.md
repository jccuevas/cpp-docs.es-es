---
title: "Colecciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas de matrices"
  - "matrices [C++], clases"
  - "clases de colección, acerca de las clases de colección"
  - "clases de colección, matrices"
  - "clases de colección, listas"
  - "clases de colección, mapas"
  - "clases de colección, MFC"
  - "clases de colección, formas"
  - "clases de colección, basadas en plantillas"
  - "colecciones, acerca de colecciones"
  - "clases de la colección MFC"
  - "MFC, colecciones"
  - "formas"
  - "formas, colección"
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Colecciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca Microsoft Foundation Class proporciona clases de colección para administrar los grupos de objetos.  Estas clases son de dos tipos:  
  
-   [Clases de colección creadas a partir de las plantillas de C\+\+](#_core_the_template.2d.based_collection_classes)  
  
-   [Clases de colección no creadas a partir de plantillas](#_core_the_collection_classes_not_based_on_templates)  
  
> [!NOTE]
>  Si el código utiliza ya clases de colección que no es de plantilla, puede continuar utilizandolas.  Si escribe las nuevas clases de colección con seguridad de tipos dispone de tipos de datos, se recomienda utilizar las nuevas clases plantilla\- basadas en.  
  
##  <a name="_core_collection_shapes"></a> Formas de colección  
 Una clase de colección se caracteriza por su “forma” y los tipos de sus elementos.  La forma hace referencia a la manera en que los objetos se organizan y que almacenados por la colección.  MFC proporciona tres formas básicas de la colección: listas, matrices, y mapas \(también conocidos como diccionarios\).  Puede elegir la colección que se adapta al problema concreto de la programación.  
  
 Cada una de las tres formas proporcionadas de colección se describe brevemente más adelante en este tema.  Para comparar las características de formas para ayudarle a decidir cuál es el mejor para el programa, vea [Recommendations for Choosing a Collection \(Clase\)](../mfc/recommendations-for-choosing-a-collection-class.md).  
  
-   Lista  
  
     La clase list proporciona una lista ordenada, el de elementos, implementada como una lista doblemente vinculada.  Una lista tiene “ejecutar” y una cola “,” y la agregar o quitar elementos de encabezado o de la cola, o insertar o eliminar elementos en el centro, es muy rápidamente.  
  
-   Matriz  
  
     La clase array proporciona una matriz dinámicamente ordenados, petición, y entero\- indizado de objetos.  
  
-   Mapa \(también conocido como diccionario\)  
  
     Un mapa es una colección que asocie un objeto clave a un objeto de valor.  
  
##  <a name="_core_the_template.2d.based_collection_classes"></a> Las clases de colección Plantilla\-basadas  
 La manera más fácil de implementar una colección de tipos que contiene objetos de cualquier tipo es utilizar una de las clases plantilla\- basadas MFC.  Para obtener ejemplos de estas clases, vea el ejemplo [GET](../top/visual-cpp-samples.md)MFC.  
  
 La tabla siguiente se enumeran las clases de colección plantilla\- basadas MFC.  
  
### Clases de plantilla de la colección  
  
|Contenido de la colección|Matrices|Listas|Mapas|  
|-------------------------------|--------------|------------|-----------|  
|Colecciones de objetos de cualquier tipo|`CArray`|`CList`|`CMap`|  
|Colecciones de punteros a objetos de cualquier tipo|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|  
  
##  <a name="_core_the_collection_classes_not_based_on_templates"></a> Las clases de colección No basado en las plantillas  
 Si la aplicación utiliza ya clases de segunda de MFC, puede continuar utilizandolas.  Sin embargo, para las nuevas colecciones, recomendamos utilizar las clases plantilla\- basadas en.  La tabla siguiente se enumeran las clases de colección de MFC que no se basan en las plantillas.  
  
### Clases de colección de Segunda  
  
|Matrices|Listas|Mapas|  
|--------------|------------|-----------|  
|`CObArray`|`CObList`|`CMapPtrToWord`|  
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|  
|`CDWordArray`|`CStringList`|`CMapStringToOb`|  
|`CPtrArray`||`CMapStringToPtr`|  
|`CStringArray`||`CMapStringToString`|  
|`CWordArray`||`CMapWordToOb`|  
|`CUIntArray`||`CMapWordToPtr`|  
  
 Las características de tabla de las clases de colección de MFC en [Recommendations for Choosing a Collection \(Clase\)](../mfc/recommendations-for-choosing-a-collection-class.md) describen las clases de colección de MFC en términos de estas características \(distinto de la forma\):  
  
-   Si la clase utiliza plantillas de C\+\+  
  
-   Si los elementos almacenados en la colección pueden ser serializados  
  
-   Si los elementos almacenados en la colección se puede volcar para diagnósticos  
  
-   Si la colección es tipo\-segura  
  
### ¿Qué desea hacer?  
  
#### Tareas de la clase de colección  
  
-   [Recommendations for Choosing a Collection \(Clase\)](../mfc/recommendations-for-choosing-a-collection-class.md)  
  
-   [Cómo: Crear una colección con seguridad de tipos](../mfc/how-to-make-a-type-safe-collection.md)  
  
-   [Crear colecciones de pila y de cola](../mfc/creating-stack-and-queue-collections.md)  
  
-   [CArray::Add](../Topic/CArray::Add.md)  
  
#### Tareas Plantilla\- basadas en la clase de colección  
  
-   [Clases basadas en plantillas](../mfc/template-based-classes.md)  
  
#### Teniendo acceso a los miembros de una colección \(Plantilla\- basada o No\)  
  
-   [Acceso a todos los miembros de una colección](../mfc/accessing-all-members-of-a-collection.md)  
  
-   [Eliminar todos los objetos de una colección CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)