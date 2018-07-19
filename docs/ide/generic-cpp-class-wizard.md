---
title: Asistente para clases genéricas de C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e86a4047ef025f49dd01eda90f324623a90752
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33328310"
---
# <a name="generic-c-class-wizard"></a>Asistente de clases genéricas de C++
Agrega una clase genérica de C++ a un proyecto. La clase no hereda de ATL o MFC.  
  
 **Nombre de la clase**  
 Establece el nombre de la clase nueva.  
  
 **Archivo .h**  
 Establece el nombre del archivo de encabezado para la clase nueva. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre de la clase**. Para guardar el archivo de encabezado en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente, haga clic en el botón de puntos suspensivos (**...**). Si se especifica un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que especifique si se debe anexar la declaración de clase al contenido del archivo. Para anexar la declaración, haga clic en **Sí**; para volver al asistente y especificar otro nombre de archivo, haga clic en **No**.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación para la clase nueva. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre de la clase**. Para guardar el archivo de implementación en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente, haga clic en el botón de puntos suspensivos (**...**). Si se especifica un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que especifique si la definición de clase se debe anexar al contenido del archivo. Para anexar la definición, haga clic en **Sí**; para volver al asistente y especificar otro nombre de archivo, haga clic en **No**.  
  
 **Clase base**  
 Establece la clase base para la clase nueva.  
  
 **Acceso**  
 Establece el acceso a los miembros de clase base para la clase nueva. Los modificadores de acceso son palabras clave que especifican el nivel de acceso que tienen otras clases a las funciones miembro de la clase. Para obtener más información sobre cómo especificar el acceso, vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md). De manera predeterminada, el nivel de acceso de la clase se establece en `public`.  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **Predeterminado** (no se genera ningún modificador de acceso).  
  
 **Destructor virtual**  
 Especifica si el destructor de clase es virtual. El uso de un destructor virtual ayuda a garantizar que se llama al destructor correcto cuando se eliminan instancias de las clases derivadas.  
  
 **Alineado**  
 Genera el constructor de clase y la definición de clase como funciones alineadas en el archivo de encabezado.  
  
 **Administrado**  
 Cuando se selecciona, agrega una clase administrada y un archivo de encabezado. Cuando se desactiva, agrega una clase nativa y un archivo de encabezado.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase genérica de C++](../ide/adding-a-generic-cpp-class.md)