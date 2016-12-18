---
title: "Especificar los niveles de funcionalidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject (clase), agregar funcionalidad a clases derivadas"
  - "compatibilidad con creación dinámica"
  - "niveles [C++]"
  - "niveles [C++], funcionalidad en CObject"
  - "tiempo de ejecución [C++], información de clases"
  - "clase en tiempo de ejecución, compatibilidad de información"
  - "serialización [C++], Cobject"
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Especificar los niveles de funcionalidad
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe cómo agregar los siguientes niveles de funcionalidad a [CObject](../mfc/reference/cobject-class.md)\- clase derivada:  
  
-   [Información de la clase en tiempo de ejecución](#_core_to_add_run.2d.time_class_information)  
  
-   [Compatibilidad dinámica de creación](#_core_to_add_dynamic_creation_support)  
  
-   [Compatibilidad de serialización](#_core_to_add_serialization_support)  
  
 Para obtener una descripción general de la funcionalidad de `CObject` , vea el artículo [Derivar de una clase de CObject](../mfc/deriving-a-class-from-cobject.md).  
  
#### Para agregar la información de la clase en tiempo de ejecución  
  
1.  Derive la clase de `CObject`, como se describe en el artículo de [Derivar de una clase de CObject](../mfc/deriving-a-class-from-cobject.md) .  
  
2.  Utilice la macro de `DECLARE_DYNAMIC` en la declaración de clase, como se muestra aquí:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/CPP/specifying-levels-of-functionality_1.h)]  
  
3.  Utilice la macro de `IMPLEMENT_DYNAMIC` en el archivo de implementación \(.CPP\) de la clase.  Esta macro toma como argumentos el nombre de clase y de su clase base, como sigue:  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/CPP/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  Coloque siempre `IMPLEMENT_DYNAMIC` en el archivo de implementación \(.CPP\) para la clase.  La macro de `IMPLEMENT_DYNAMIC` se debe evaluar solo una vez durante una compilación y por consiguiente no se debe utilizar en un archivo de interfaz \(. H\) que se podría incluir en más de un archivo.  
  
#### Para agregar compatibilidad dinámica de creación  
  
1.  Derive la clase de `CObject`.  
  
2.  Utilice la macro de `DECLARE_DYNCREATE` en la declaración de clase.  
  
3.  Defina un constructor sin argumentos \(un constructor predeterminado\).  
  
4.  Utilice la macro de `IMPLEMENT_DYNCREATE` en el archivo de implementación de la clase.  
  
#### Para agregar compatibilidad de serialización  
  
1.  Derive la clase de `CObject`.  
  
2.  Reemplace la función miembro de `Serialize` .  
  
    > [!NOTE]
    >  Si llama a `Serialize` directamente, es decir, no desea serializar el objeto mediante un puntero polimórfico, omite los pasos 3 a 5.  
  
3.  Utilice la macro de `DECLARE_SERIAL` en la declaración de clase.  
  
4.  Defina un constructor sin argumentos \(un constructor predeterminado\).  
  
5.  Utilice la macro de `IMPLEMENT_SERIAL` en el archivo de implementación de la clase.  
  
> [!NOTE]
>  Puntos de un “puntero polimórfico” a un objeto de una clase \(llamada A\) o un objeto de cualquier clase derivada de \(indica, B\).  Para serializar mediante un puntero polimórfico, el marco debe determinar la clase en tiempo de ejecución del objeto que está serializando \(b\), ya que puede ser un objeto de cualquier clase derivada de alguna clase base \(a\).  
  
 Para obtener más información sobre cómo habilitar la serialización cuando derive la clase de `CObject`, vea los artículos [Archivos en MFC](../mfc/files-in-mfc.md) y [Serialización](../mfc/serialization-in-mfc.md).  
  
## Vea también  
 [Derivar una clase de CObject](../mfc/deriving-a-class-from-cobject.md)