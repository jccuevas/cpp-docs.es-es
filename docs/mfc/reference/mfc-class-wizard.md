---
title: Asistente para clases MFC | Microsoft Docs
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
ms.openlocfilehash: b06353f7e0756cadb6ad05e1e5b35b3cd36b526c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725158"
---
# <a name="mfc-class-wizard"></a>Asistente para clases MFC
Le permite agregar mensajes y controladores de mensajes a las clases del proyecto. Puede iniciar también otros asistentes o agregar una clase al proyecto.  
  
 Para abrir el **Asistente para clases MFC**, en el **proyecto** menú, haga clic en **Class Wizard**. Para abrir el asistente con un método abreviado de teclado, use CTRL+MAYÚS+X.  
  
## <a name="uielement-list"></a>Lista de UIElement

- **Proyecto**

   Nombre de un proyecto de la solución.  
  
   Puede seleccionar otros proyectos de la solución en el cuadro de lista desplegable.  
  
- **Nombre de la clase**

   Nombre de una clase en el proyecto.  
  
   Al seleccionar una clase en el **nombre de la clase** rellenan de datos de la clase de lista, los controles en el **Asistente para clases MFC**. Al cambiar el valor de un control, se ven afectados los datos de la clase seleccionada.  
  
- **Agregar clase**

   Le permite agregar una clase desde uno de varios orígenes.  
  
   Según su selección, el **Asistente para agregar clases de MFC**, **Asistente para agregar clases de la biblioteca de tipos**, **Agregar clase de Asistente para controles ActiveX**, o **ODBC de MFC Asistente para consumidores** se inicia.  
  
- **Clase base**

   La clase base de la clase que se muestra en **nombre de la clase**.  
  
- **Declaración de clase**

   La clase en la que el **nombre de la clase** clase se declara.  
  
   El **declaración de clase** cuadro se muestra solo si el nombre de la que difiere del nombre en **implementación de la clase**.  
  
- **Recurso**

   El identificador del recurso en **nombre de la clase**, si la hubiera. En caso contrario, el **recursos** cuadro está vacío.  
  
- **Implementación de la clase**

   El nombre del archivo que contiene la implementación de la clase en **nombre de la clase**.  
  
   Puede seleccionar un archivo de implementación diferente si hace clic en la flecha. En la siguiente tabla se enumeran las opciones disponibles.  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Abrir archivo**|Sale del asistente para clases y abre el archivo de implementación de clase actual.|  
   |**Abrir carpeta contenedora**|Abre la carpeta que contiene el archivo de implementación de clase actual.|  
   |**Copiar ruta de acceso completa en el Portapapeles**|Copia la ruta de acceso del archivo de implementación actual en el Portapapeles.|  
  
- **Comandos**

   Le permite agregar, eliminar, editar o buscar un comando y su controlador de mensajes.  
  
   Para agregar un controlador, haga clic en **Agregar controlador**, o haga doble clic en un elemento en el **los identificadores de objeto** lista o **mensajes** lista. Nombre de la función, identificador y mensaje resultantes se muestran en el **funciones miembro** lista.  
  
   Para eliminar un controlador, seleccione un elemento en el **funciones miembro** lista y, a continuación, haga clic en **eliminar controlador**.  
  
   Para modificar un controlador, haga doble clic en el elemento correspondiente en el **funciones miembro** lista. O bien, seleccione un elemento en el cuadro de lista y, a continuación, haga clic en **modificar código**.  
  
- **Mensajes**

   Le permite agregar, eliminar, editar o buscar un mensaje y su controlador de mensajes.  
  
   Para agregar un controlador, haga clic en **Agregar controlador**, o haga doble clic en un elemento en el **mensajes** lista.  
  
   Para agregar un mensaje personalizado, haga clic en **Agregar mensaje personalizado** o presione la tecla ENTRAR y, a continuación, especifique los valores en el **Agregar mensaje personalizado** cuadro de diálogo. Este cuadro de diálogo, puede seleccionar también **mensaje registrado** para controlar un mensaje de ventana que se garantiza que sea único en todo el sistema operativo.  
  
- **Funciones virtuales**

   Le permite agregar, eliminar, editar o buscar una función virtual o una función virtual invalidada.  
  
- **Variables de miembro**

   Le permite agregar, eliminar, editar o buscar una variable de miembro.  
  
- **Métodos**

   Le permite agregar, eliminar o buscar un método y también ir a la definición o declaración de un método.  
  
   Para agregar un método, haga clic en **Agregar método**y, a continuación, especifique los valores en el **Agregar método** cuadro de diálogo.  
  
   Para eliminar un método, seleccione un elemento en el **métodos** lista y, a continuación, haga clic en **método Delete**.  
  
   Para mostrar una declaración, seleccione un elemento en el **métodos** lista y, a continuación, haga clic en **ir a declaración.**  
  
   Para mostrar una definición, haga doble clic en un elemento en el **métodos** lista. O bien, seleccione un elemento en el **métodos** lista y, a continuación, haga clic en el **ir a definición** botón.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)
