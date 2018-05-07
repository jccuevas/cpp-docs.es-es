---
title: Asistente para clases genéricas de C++ | Documentos de Microsoft
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
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="generic-c-class-wizard"></a>Asistente de clases genéricas de C++
Agrega una clase genérica de C++ a un proyecto. La clase no hereda de ATL o MFC.  
  
 **Nombre de clase**  
 Establece el nombre de la nueva clase.  
  
 **archivo .h**  
 Establece el nombre del archivo de encabezado para la nueva clase. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre de la clase**. Para guardar el archivo de encabezado en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente, haga clic en el botón de puntos suspensivos (**...** ). Si se especifica un archivo existente, al hacer clic en **finalizar**, el asistente le pedirá que especifique si se debe anexar la declaración de clase para el contenido del archivo. Para anexar la declaración, haga clic en **Sí**; para volver al asistente y especificar otro nombre de archivo, haga clic en **No**.  
  
 **archivo .cpp**  
 Establece el nombre del archivo de implementación para la nueva clase. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre de la clase**. Para guardar el archivo de implementación en la ubicación de su elección, o para anexar la definición de clase a un archivo existente, haga clic en el botón de puntos suspensivos (**...** ). Si se especifica un archivo existente, al hacer clic en **finalizar**, el asistente le pedirá que especifique si se debe anexar a la definición de clase para el contenido del archivo. Para anexar la definición, haga clic en **Sí**; para volver al asistente y especificar otro nombre de archivo, haga clic en **No**.  
  
 **Clase base**  
 Establece la clase base para la nueva clase.  
  
 **Acceso**  
 Establece el acceso a los miembros de clase base para la nueva clase. Modificadores de acceso son palabras clave que especifican el nivel de acceso que tienen otras clases a las funciones de miembro de clase. Para obtener más información acerca de cómo especificar el acceso, consulte [Control de acceso de miembro](../cpp/member-access-control-cpp.md). De forma predeterminada, el nivel de acceso de clase se establece en `public`.  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **Predeterminado** (no se genera ningún modificador de acceso).  
  
 **Destructor virtual**  
 Especifica si el destructor de clase es virtual. Uso de un destructor virtual ayuda a garantizar que se llama al destructor correcto cuando se eliminan instancias de clases derivadas.  
  
 **En línea**  
 Genera el constructor de clase y la definición de clase como funciones inline en el archivo de encabezado.  
  
 **Administrado**  
 Cuando se selecciona, agrega un archivo de encabezado y de clase administrado. Cuando está desactivada, se agrega un archivo de clase y encabezado nativo.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase genérica de C++](../ide/adding-a-generic-cpp-class.md)