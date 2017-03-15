---
title: "Clases de matriz, lista y mapa | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], clases"
  - "clases de colección, listas"
  - "clases de colección, mapas"
  - "lista de clases"
  - "map (clases)"
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Clases de matriz, lista y mapa
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para administrar los agregados de datos, la biblioteca de clases de proporciona a un grupo de clases de colección — matrices, listas, y los mapas \)que pueden contener una variedad de objeto y de tipos predefinidos.  Las colecciones se ordenan dinámicamente.  Estas clases se pueden utilizar en cualquier programa, están escritas para Windows o no.  Sin embargo, son muy útiles para implementar las estructuras de datos que definen las clases de documento en el marco de trabajo de la aplicación.  Puede derivar fácilmente clases de colección especializadas de éstos, o puede crearlos basándose en las clases de plantilla.  Para obtener más información sobre estos enfoques, vea el artículo [Colecciones](../mfc/collections.md).  Para obtener una lista de las clases de colección de plantillas, vea el artículo [Clases de plantilla para matrices, listas, y mapas](../mfc/template-classes-for-arrays-lists-and-maps.md).  
  
 Las matrices son estructuras de datos unidimensionales que se almacenan de forma contigua en memoria.  Admiten acceso aleatorio muy rápido desde la dirección de memoria de cualquier elemento determinado puede calcular multiplicando el índice del elemento por el tamaño de un elemento y agregando el resultado a la dirección base de la matriz.  Pero las matrices son muy costosas si tiene que insertar elementos en la matriz, ya que la matriz completa más allá del elemento insertado tiene que mover para hacer sitio para el elemento que se desea insertar.  Las matrices pueden crecer y reduzca según sea necesario.  
  
 Las listas son similares a las matrices pero se almacenan muy de manera diferente.  Cada elemento de una lista también incluye un puntero a los elementos anteriores y siguientes, en una lista doblemente vinculada.  Es muy rápidamente agregar o eliminar elementos puesto que implica tan solo el cambiar de algunos punteros.  Sin embargo, buscar una lista puede ser costoso puesto que todas las búsquedas necesitan iniciar en uno de los extremos de la lista.  
  
 Los mapas se relacionan un valor de clave con un valor de datos.  Por ejemplo, la clave de un mapa podría ser una cadena y los datos un puntero en una lista.  Se pediría el mapa para proporcionar el puntero asociado a una cadena concreta.  Las búsquedas de mapa son rápidas porque los mapas utilizan las tablas hash para las búsquedas clave.  Agregar y eliminar elementos también es rápidas.  Los mapas se suelen usar con otras estructuras de datos como índices auxiliares.  MFC utiliza una clase especial de mapa denominada [mapa de mensajes](../mfc/mapping-messages.md) para asignar los mensajes de Windows en un puntero a la función controladora para ese mensaje.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)