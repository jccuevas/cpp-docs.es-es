---
title: "Derivar una clase de CObject | Microsoft Docs"
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
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject (clase), derivar de"
  - "CObject (clase), derivar clases serializables"
  - "DECLARE_DYNAMIC (macro)"
  - "DECLARE_DYNCREATE (macro)"
  - "DECLARE_SERIAL (macro)"
  - "clases derivadas, desde CObject"
  - "macros [C++], serialización"
  - "serialización [C++], macros"
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Derivar una clase de CObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe los pasos mínimos necesarios derivar una clase de [CObject](../mfc/reference/cobject-class.md).  Otros casos de la clase de `CObject` describen los pasos necesarios para aprovechar las características específicas de `CObject` , como serialización y compatibilidad de diagnóstico de depuración.  
  
 En las conversaciones de `CObject`, los términos “archivo de interfaz” y “archivo de implementación” se utilizan con frecuencia.  El archivo de interfaz \(a menudo denominado el archivo de encabezado, o. El archivo de h\) contiene la declaración de clase y cualquier otra información necesarias para utilizar la clase.  El archivo de implementación \(o el archivo de .CPP\) contiene la definición de clase y el código que implementa el miembro de clase funciona.  Por ejemplo, porque una clase denominada `CPerson`, crearía normalmente un archivo de interfaz denominado PERSON.H y el archivo de implementación denominado PERSON.CPP.  Sin embargo, para algunas pequeñas clases que no sean compartidas entre aplicaciones, a veces es más fácil combinar la interfaz e implementación en un solo archivo de .CPP.  
  
 Puede elegir entre de cuatro niveles de funcionalidad al derivar una clase de `CObject`:  
  
-   Funcionalidad básica: Compatibilidad para la información o la serialización de la clase en tiempo de ejecución pero incluye la administración de memoria de diagnóstico.  
  
-   Funcionalidad básica más compatibilidad con la información de la clase en tiempo de ejecución.  
  
-   Funcionalidad básica más compatibilidad con la información de la clase en tiempo de ejecución y asignación dinámica.  
  
-   Funcionalidad básica más compatibilidad con la información de la clase en tiempo de ejecución, la creación dinámica, y la serialización.  
  
 Clases diseñadas para su reutilización \(las que servirá después como clases base\) deben incluir por lo menos la compatibilidad con la clase en tiempo de ejecución y la compatibilidad de serialización, si se prevé alguna necesidad futura de serialización.  
  
 Elija el nivel de funcionalidad mediante macros específicas de declaración e implementación en la declaración y la implementación de las clases que deriva de `CObject`.  
  
 La tabla siguiente muestra la relación entre las macros utilizadas para la serialización admiten e información del tiempo de ejecución.  
  
### Macros utilizadas para la serialización y la información en tiempo de ejecución  
  
|Macro utilizada|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator\>\><br /><br /> CArchive::operator\<\<|  
|---------------------|-----------------------|--------------------------------------|-------------------------------------------------------|  
|Funcionalidad básica de `CObject`|No|No|No|  
|`DECLARE_DYNAMIC`|Sí|No|No|  
|`DECLARE_DYNCREATE`|Sí|Sí|No|  
|`DECLARE_SERIAL`|Sí|Sí|Sí|  
  
#### Para utilizar la funcionalidad básica de CObject  
  
1.  Utilice la sintaxis normal de C\+\+ para derivar la clase de `CObject` \(o una clase derivada de `CObject`\).  
  
     El ejemplo siguiente se muestra el caso más simple, la derivación de una clase de `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/CPP/deriving-a-class-from-cobject_1.h)]  
  
 Normalmente, sin embargo, puede que desee invalidar algunas de las funciones miembro de `CObject` para controlar los detalles de la nueva clase.  Por ejemplo, puede que desee normalmente para reemplazar la función de `Dump` de `CObject` para proporcionar la depuración generada por el contenido de la clase.  Para obtener información sobre cómo invalidar `Dump`, vea el artículo [Diagnostics: Volcar contenido del objeto](http://msdn.microsoft.com/es-es/727855b1-5a83-44bd-9fe3-f1d535584b59).  Puede que también desee reemplazar la función de `AssertValid` de `CObject` para proporcionar pruebas personalizadas para validar la coherencia de los miembros de datos de objetos de clase.  Para obtener una descripción de cómo reemplazar `AssertValid`, vea [MFC ASSERT\_VALID y CObject::AssertValid](http://msdn.microsoft.com/es-es/7654fb75-9e9a-499a-8165-0a96faf2d5e6).  
  
 El artículo [Especificar niveles de funcionalidad](../mfc/specifying-levels-of-functionality.md) describe cómo especificar otros niveles de funcionalidad, incluida la información de la clase en tiempo de ejecución, la creación de objetos dinámica, y la serialización.  
  
## Vea también  
 [Usar CObject](../mfc/using-cobject.md)