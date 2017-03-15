---
title: "Asistente para clases MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.wizards.classwizard"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para clases MFC"
  - "asistentes (MFC)"
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Asistente para clases MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Le permite agregar mensajes y controladores de mensajes a las clases del proyecto.  Puede iniciar también otros asistentes o agregar una clase al proyecto.  
  
 Para abrir el **Asistente para clases MFC**, en el menú **Proyecto**, haga clic en **Asistente para clases**.  Para abrir el asistente con un método abreviado de teclado, use CTRL\+MAYÚS\+X.  
  
## Lista de UIElement  
 **Proyecto**  
 Nombre de un proyecto de la solución.  
  
 Puede seleccionar otros proyectos de la solución en el cuadro de lista desplegable.  
  
 **Nombre de clase**  
 Nombre de una clase en el proyecto.  
  
 Al seleccionar una clase en la lista **Nombre de clase**, los datos de la clase rellenan los controles del **Asistente para clases MFC**.  Al cambiar el valor de un control, se ven afectados los datos de la clase seleccionada.  
  
 **Agregar clase**  
 Le permite agregar una clase desde uno de varios orígenes.  
  
 Dependiendo de su selección, se inicia el **Asistente para agregar clases MFC**, el **Asistente para agregar clases de la biblioteca de tipos**, el **Asistente para agregar clases a partir de un control ActiveX** o el **Asistente para consumidores ODBC MFC**.  
  
 **Clase base**  
 Clase base de la clase que se muestra en **Nombre de clase**.  
  
 **Declaración de clase**  
 La clase en la que se declara la clase **Nombre de clase**.  
  
 El cuadro **Declaración de clase** solo se muestra si el nombre que contiene es diferente del nombre de **Implementación de clase**.  
  
 **Recurso**  
 El identificador del recurso en **Nombre de clase**, si existe.  De lo contrario, el cuadro **Recurso** está vacío.  
  
 **Implementación de clase**  
 Nombre del archivo que contiene la implementación de la clase de **Nombre de clase**.  
  
 Puede seleccionar un archivo de implementación diferente si hace clic en la flecha.  En la siguiente tabla se enumeran las opciones disponibles.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Abrir archivo**|Sale del asistente para clases y abre el archivo de implementación de clase actual.|  
|**Abrir carpeta Contenido**|Abre la carpeta que contiene el archivo de implementación de clase actual.|  
|**Copiar ruta de acceso completa en el Portapapeles**|Copia la ruta de acceso del archivo de implementación actual en el Portapapeles.|  
  
 **Comandos**  
 Le permite agregar, eliminar, editar o buscar un comando y su controlador de mensajes.  
  
 Para agregar un controlador, haga clic en **Agregar controlador** o haga doble clic en un elemento de la lista **Identificadores de objeto** o **Mensajes**.  El nombre de función, identificador y mensaje resultantes se muestran en la lista **Funciones miembro**.  
  
 Para eliminar un controlador, seleccione un elemento de la lista **Funciones miembro** y, a continuación, haga clic en **Eliminar controlador**.  
  
 Para modificar un controlador, haga doble clic en el elemento correspondiente en la lista **Funciones miembro**.  O bien, seleccione un elemento del cuadro de lista y, a continuación, haga clic en **Editar código**.  
  
 **Mensajes**  
 Le permite agregar, eliminar, editar o buscar un mensaje y su controlador de mensajes.  
  
 Para agregar un controlador, haga clic en **Agregar controlador** o haga doble clic en un elemento en la lista **Mensajes**.  
  
 Para agregar un mensaje personalizado, haga clic en **Agregar mensaje personalizado** o presione la tecla Entrar y, a continuación, especifique los valores en el cuadro de diálogo **Agregar mensaje personalizado**.  En ese cuadro de diálogo, puede seleccionar también **Mensaje registrado** para administrar un mensaje de ventana que se garantiza que es único en todo el sistema operativo.  
  
 **Funciones virtuales**  
 Le permite agregar, eliminar, editar o buscar una función virtual o una función virtual invalidada.  
  
 **Variables de miembro**  
 Le permite agregar, eliminar, editar o buscar una variable de miembro.  
  
 **Métodos**  
 Le permite agregar, eliminar o buscar un método y también ir a la definición o declaración de un método.  
  
 Para agregar un método, haga clic en **Agregar método** y, a continuación, especifique los valores en el cuadro de diálogo **Agregar método**.  
  
 Para eliminar un método, seleccione un elemento de la lista **Métodos** y, a continuación, haga clic en **Eliminar método**.  
  
 Para mostrar una declaración, seleccione un elemento de la lista **Métodos** y, a continuación, haga clic **Ir a declaración**.  
  
 Para mostrar una definición, haga doble clic en un elemento de la lista **Métodos**.  O bien, seleccione un elemento de la lista **Métodos** y, a continuación, haga clic en el botón **Ir a definición**.  
  
## Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)