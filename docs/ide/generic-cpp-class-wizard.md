---
title: "Asistente de clases gen&#233;ricas de C++ | Microsoft Docs"
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
  - "vc.codewiz.class.generic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para clases genéricas [C++]"
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente de clases gen&#233;ricas de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega una clase genérica de C\+\+ a un proyecto.  La clase no hereda de ATL o MFC.  
  
 **Nombre de la clase**  
 Define el nombre de la nueva clase.  
  
 **Archivo .H**  
 Establece el nombre del archivo de encabezado de la nueva clase.  De forma predeterminada, este nombre está basado en el nombre proporcionado en **Nombre de clase**.  Para guardar el archivo de encabezado en la ubicación que desee o para guardar la declaración de clase en un archivo existente, haga clic en el botón de puntos suspensivos \(**...**\).  Si especifica un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea especificar la declaración de la clase al contenido del archivo.  Para anexar la declaración, haga clic en **Sí**; para volver al asistente y especificar otro nombre de archivo, haga clic en **No**.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación de la nueva clase.  De forma predeterminada, este nombre está basado en el nombre proporcionado en **Nombre de clase**.  Para guardar el archivo de implementación en la ubicación que desee o para anexar la definición de clase a un archivo existente, haga clic en el botón de puntos suspensivos \(**...**\).  Si especifica un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea especificar la definición de la clase al contenido del archivo.  Para anexar la definición, haga clic en **Sí**; para volver al asistente y especificar otro nombre de archivo, haga clic en **No**.  
  
 **Clase base**  
 Define la clase base de la clase nueva.  
  
 **Acceso**  
 Define el acceso a los miembros de la clase base de la clase nueva.  Los modificadores de acceso son palabras clave que especifican el nivel de acceso que tienen otras clases a las funciones miembro de la clase.  Para obtener más información acerca de cómo especificar el acceso, vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md).  De forma predeterminada, el nivel de acceso a la clase está establecido en `public`.  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **Predeterminado** \(No se genera ningún modificador de acceso\).  
  
 **Destructor virtual**  
 Especifica si el destructor de la clase es virtual.  El uso de un destructor virtual permite asegurar que se llama al destructor correcto cuando se eliminan instancias de las clases derivadas.  
  
 **En línea**  
 Genera el constructor y la definición de clase como funciones inline en el archivo de encabezado.  
  
 **Administrado**  
 Cuando se selecciona, agrega una clase administrada y un archivo de encabezado.  Cuando está desactivada, agrega una clase nativa y un archivo de encabezado.  
  
## Vea también  
 [Agregar una clase genérica de C\+\+](../ide/adding-a-generic-cpp-class.md)