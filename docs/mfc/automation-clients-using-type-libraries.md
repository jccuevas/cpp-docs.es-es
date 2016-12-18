---
title: "Clientes de automatizaci&#243;n: Usar bibliotecas de tipos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MkTypLib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos .odl"
  - "clientes de automatización, bibliotecas de tipos"
  - "clases [C++], envío"
  - "clientes, automatización"
  - "clase de envío"
  - "MkTypLib (herramienta)"
  - "ODL (lenguaje de descripción de objetos)"
  - "ODL (archivos)"
  - "bibliotecas de tipos, clientes de automatización"
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clientes de automatizaci&#243;n: Usar bibliotecas de tipos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los clientes de automatización deben tener información sobre las propiedades y los métodos de los objetos de servidor si los clientes deben manipular los objetos de los servidores.  Las propiedades tienen tipos de datos; de los métodos devolverán valores a menudo y aceptan parámetros.  El cliente necesita información sobre tipos de datos de todas estas para vincular estáticamente al tipo de objeto de servidor.  
  
 Esta información de tipo se puede asignar a conocer de varias maneras.  La forma recomendada es crear una biblioteca de tipos.  
  
 Para obtener información sobre [MkTypLib](http://msdn.microsoft.com/library/windows/desktop/aa366797), vea [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Visual C\+\+ puede leer un archivo de biblioteca de tipos y crear una clase de envío derivada de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md).  Un objeto de esa clase tiene propiedades y operaciones que duplican el objeto de servidor.  La aplicación llama a esto propiedades y las operaciones del objeto, y la funcionalidad heredada de `COleDispatchDriver` distribuya estas llamadas al sistema OLE, que a su vez las encamine al objeto de servidor.  
  
 Visual C\+\+ automáticamente mantiene este archivo de biblioteca de tipos para se si decide incluir automatización cuando el proyecto se creó.  Como parte de cada compilación, el archivo .tlb se compilará con MkTypLib.  
  
### Para crear una clase de enviar un archivo de biblioteca de tipos \(.tlb\)  
  
1.  En la vista o el explorador de soluciones de clases, haga clic con el botón secundario en el proyecto y el tecleo **Add** y haga clic en **Agregar clase** en el menú contextual.  
  
2.  En el cuadro de diálogo de **Agregar clase** , seleccione la carpeta de **Visual C\+\+\/MFC** en el panel izquierdo.  Seleccione el icono de **Clase MFC de TypeLib** en el panel derecho y haga clic en **Abierta**.  
  
3.  En el cuadro de diálogo de **Asistente para agregar clases de la biblioteca de tipos** , seleccione una biblioteca de tipos en la lista desplegable de **Available type libraries** .  El cuadro de **Interfaces** muestra las interfaces disponibles para la biblioteca de tipos seleccionada.  
  
    > [!NOTE]
    >  Puede seleccionar interfaces de más de una biblioteca de tipos.  
  
     A las interfaces de selección, haga doble clic o haga clic en el botón de **Add** .  Si lo hace, los nombres de las clases de envío aparecerán en el cuadro de **Clases generadas** .  Puede modificar los nombres de clase en el cuadro de `Class` .  
  
     El cuadro de **archivo** muestra el archivo en el que la clase se declara. \(puede modificar este nombre de archivo también\).  También puede utilizar el botón examinar para seleccionar otros archivos, si prefiere que el encabezado y la información de implementación escritos en archivos existentes o en un directorio distinto del directorio de proyecto.  
  
    > [!NOTE]
    >  Todas las clases de envío para las interfaces seleccionado se colocan en el archivo especificado aquí.  Si desea que las interfaces que se declararán en encabezados independientes, debe ejecutar este asistente para cada archivo de encabezado que desea crear.  
  
    > [!NOTE]
    >  Alguna información de biblioteca de tipos se puede almacenar en archivos con las extensiones de archivo .DLL, de .OCX, o de .OLB.  
  
4.  Haga clic en **Finalizar**.  
  
     Después el asistente escribirá código para las clases de distribución mediante la clase y los nombres de archivo especificados.  
  
## Vea también  
 [Clientes de automatización](../mfc/automation-clients.md)