---
title: Asistente para clases MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.wizards.classwizard
dev_langs:
- C++
helpviewer_keywords:
- wizards (MFC)
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 409fd7f0cde2090b84ed2a997fedc43b2ffd5db7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-class-wizard"></a>Asistente para clases MFC
Le permite agregar mensajes y controladores de mensajes a las clases del proyecto. Puede iniciar también otros asistentes o agregar una clase al proyecto.  
  
 Para abrir el **Asistente para clases MFC**, en la **proyecto** menú, haga clic en **Asistente para clases**. Para abrir el asistente con un método abreviado de teclado, use CTRL+MAYÚS+X.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Proyecto**  
 Nombre de un proyecto de la solución.  
  
 Puede seleccionar otros proyectos de la solución en el cuadro de lista desplegable.  
  
 **Nombre de clase**  
 Nombre de una clase en el proyecto.  
  
 Al seleccionar una clase en el **nombre de la clase** lista, los datos de la clase rellenan los controles en el **Asistente para clases MFC**. Al cambiar el valor de un control, se ven afectados los datos de la clase seleccionada.  
  
 **Agregar clase**  
 Le permite agregar una clase desde uno de varios orígenes.  
  
 Según su selección, el **Asistente para agregar clases de MFC**, **Asistente para agregar clases de la biblioteca de tipos**, **Agregar clase de Asistente para controles ActiveX**, o **ODBC de MFC Asistente para consumidores** se inicia.  
  
 **Clase base**  
 La clase base de la clase que se muestra en **nombre de la clase**.  
  
 **Declaración de clase**  
 La clase en la que el **nombre de la clase** clase se declara.  
  
 El **declaración de clase** cuadro solo se muestra si el nombre es diferente del nombre de **implementación de la clase**.  
  
 **Recursos**  
 El identificador del recurso en **nombre de la clase**, si existe. En caso contrario, el **recursos** cuadro está vacío.  
  
 **Implementación de la clase**  
 El nombre del archivo que contiene la implementación de la clase en **nombre de la clase**.  
  
 Puede seleccionar un archivo de implementación diferente si hace clic en la flecha. En la siguiente tabla se enumeran las opciones disponibles.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Abrir archivo**|Sale del asistente para clases y abre el archivo de implementación de clase actual.|  
|**Abrir carpeta contenido**|Abre la carpeta que contiene el archivo de implementación de clase actual.|  
|**Copiar ruta de acceso completa al Portapapeles**|Copia la ruta de acceso del archivo de implementación actual en el Portapapeles.|  
  
 **Comandos**  
 Le permite agregar, eliminar, editar o buscar un comando y su controlador de mensajes.  
  
 Para agregar un controlador, haga clic en **Agregar controlador**, o haga doble clic en un elemento en el **identificadores de objeto** lista o **mensajes** lista. Nombre de la función, identificador y mensaje resultantes se muestran en la **funciones miembro** lista.  
  
 Para eliminar un controlador, seleccione un elemento en el **funciones miembro** lista y, a continuación, haga clic en **eliminar controlador**.  
  
 Para modificar un controlador, haga doble clic en el elemento correspondiente de la **funciones miembro** lista. O bien, seleccione un elemento en el cuadro de lista y, a continuación, haga clic en **editar código**.  
  
 **Mensajes**  
 Le permite agregar, eliminar, editar o buscar un mensaje y su controlador de mensajes.  
  
 Para agregar un controlador, haga clic en **Agregar controlador**, o haga doble clic en un elemento en el **mensajes** lista.  
  
 Para agregar un mensaje personalizado, haga clic en **Agregar mensaje personalizado** o presione la tecla ENTRAR y, a continuación, especifique los valores en el **Agregar mensaje personalizado** cuadro de diálogo. Este cuadro de diálogo, puede seleccionar también **mensaje registrado** para controlar un mensaje de ventana que se garantiza que sea único en todo el sistema operativo.  
  
 **Funciones virtuales**  
 Le permite agregar, eliminar, editar o buscar una función virtual o una función virtual invalidada.  
  
 **Variables de miembro**  
 Le permite agregar, eliminar, editar o buscar una variable de miembro.  
  
 **Métodos**  
 Le permite agregar, eliminar o buscar un método y también ir a la definición o declaración de un método.  
  
 Para agregar un método, haga clic en **Agregar método**y, a continuación, especifique los valores en el **Agregar método** cuadro de diálogo.  
  
 Para eliminar un método, seleccione un elemento en el **métodos** lista y, a continuación, haga clic en **método Delete**.  
  
 Para mostrar una declaración, seleccione un elemento en el **métodos** lista y, a continuación, haga clic en **ir a declaración.**  
  
 Para mostrar una definición, haga doble clic en un elemento en el **métodos** lista. O bien, seleccione un elemento en el **métodos** lista y, a continuación, haga clic en el **ir a definición** botón.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)
