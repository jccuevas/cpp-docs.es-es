---
title: Asistente para clases MFC
ms.date: 09/06/2019
f1_keywords:
- vc.wizards.classwizard
helpviewer_keywords:
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
ms.openlocfilehash: be829156d8fea8188a217b2c0a189ac5d6057a7e
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907993"
---
# <a name="mfc-class-wizard"></a>Asistente para clases MFC

Use el **Asistente para clases** para crear clases MFC nuevas o agregar mensajes y controladores de mensajes a las clases existentes en el proyecto.

Hay tres maneras de abrir el **Asistente para clases**:

- En el menú **proyecto** , elija **Asistente para clases**.
- Presione **Ctrl** > MAYÚSX > .
- En **vista de clases**, haga clic con el botón derecho en una clase o en el nodo del proyecto y elija **Asistente para clases**.

![Asistente para clases](media/class-wizard.png "Asistente para clases MFC")

## <a name="uielement-list"></a>Lista de UIElement

- **Proyecto**

   Nombre de un proyecto de la solución.

   Puede seleccionar otros proyectos de la solución en el cuadro de lista desplegable.

- **Nombre de la clase**

   Nombre de una clase en el proyecto.

   Al seleccionar una clase en la lista **nombre de clase** , los datos de la clase rellenan los controles del **Asistente para clases MFC**. Al cambiar el valor de un control, se ven afectados los datos de la clase seleccionada.

- **Agregar clase**

   Permite agregar una nueva clase al proyecto MFC.

- **Clase base**

   La clase base de la clase que se muestra en **nombre de clase**.

- **Declaración de clase**

   Clase en la que se declara la clase de **nombre de clase** .

   Solo se muestra el cuadro **declaración de clase** si el nombre en él difiere del nombre de la implementación de la **clase**.

- **Recurso**

   IDENTIFICADOR del recurso en el nombre de la **clase**, si existe. De lo contrario, el cuadro de **recurso** está vacío.

- **Implementación de clase**

   Nombre del archivo que contiene la implementación de la clase en el **nombre de clase**.

   Puede seleccionar un archivo de implementación diferente si hace clic en la flecha. En la siguiente tabla se enumeran las opciones disponibles.

   |Opción|DESCRIPCIÓN|
   |------------|-----------------|
   |**Abrir archivo**|Sale del asistente para clases y abre el archivo de implementación de clase actual.|
   |**Abrir carpeta contenedora**|Abre la carpeta que contiene el archivo de implementación de clase actual.|
   |**Copiar ruta de acceso completa al portapapeles**|Copia la ruta de acceso del archivo de implementación actual en el Portapapeles.|

- **Comandos**

   Le permite agregar, eliminar, editar o buscar un comando y su controlador de mensajes.

   Para agregar un controlador, haga clic en **Agregar controlador**o haga doble clic en un elemento en la lista de **identificadores de objetos** o en la lista de **mensajes** . El nombre de función, el ID. y el mensaje resultantes se muestran en la lista de **funciones miembro** .

   Para eliminar un controlador, seleccione un elemento en la lista **funciones miembro** y, a continuación, haga clic en **eliminar controlador**.

   Para modificar un controlador, haga doble clic en el elemento correspondiente en la lista **funciones miembro** . O bien, seleccione un elemento en el cuadro de lista y, a continuación, haga clic en **editar código**.

- **Mensajes**

   Le permite agregar, eliminar, editar o buscar un mensaje y su controlador de mensajes.

   Para agregar un controlador, haga clic en **Agregar controlador**o haga doble clic en un elemento de la lista de **mensajes** .

   Para agregar un mensaje personalizado, haga clic en **Agregar mensaje personalizado** o presione la tecla entrar y, a continuación, especifique los valores en el cuadro de diálogo **Agregar mensaje personalizado** . En ese cuadro de diálogo, también puede seleccionar **mensaje registrado** para controlar un mensaje de ventana que se garantiza que es único en todo el sistema operativo.

- **Funciones virtuales**

   Le permite agregar, eliminar, editar o buscar una función virtual o una función virtual invalidada.

- **Variables de miembro**

   Le permite agregar, eliminar, editar o buscar una variable de miembro.

- **Métodos**

   Le permite agregar, eliminar o buscar un método y también ir a la definición o declaración de un método.

   Para agregar un método, haga clic en **Agregar método**y, a continuación, especifique los valores en el cuadro de diálogo **Agregar método** .

   Para eliminar un método, seleccione un elemento en la lista **métodos** y, a continuación, haga clic en **Eliminar método**.

   Para mostrar una declaración, seleccione un elemento en la lista **métodos** y, a continuación, haga clic en **ir a declaración.**

   Para mostrar una definición, haga doble clic en un elemento de la lista de **métodos** . O bien, seleccione un elemento en la lista **métodos** y, a continuación, haga clic en el botón **ir a definición** .

## <a name="see-also"></a>Vea también

[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)
