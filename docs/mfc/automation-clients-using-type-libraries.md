---
title: 'Los clientes de automatización: Usar bibliotecas de tipos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MkTypLib
dev_langs:
- C++
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67fa0f5d164ae325caff576fb41695fc8689fda0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="automation-clients-using-type-libraries"></a>Clientes de Automation: Usar bibliotecas de tipos
Los clientes de automatización deben tener información sobre propiedades y métodos de objetos de servidor si los clientes son manipular objetos de los servidores. Propiedades tienen tipos de datos; a menudo, los métodos devuelven valores y aceptan parámetros. El cliente requiere información sobre los tipos de datos de todos estos para vincular estáticamente para el tipo de objeto de servidor.  
  
 Esta información de tipo puede dar a conocer de varias maneras. La manera recomendada es crear una biblioteca de tipos.  
  
 Para obtener información sobre [MkTypLib](http://msdn.microsoft.com/library/windows/desktop/aa366797), consulte el SDK de Windows.  
  
 Visual C++ puede leer un archivo de biblioteca de tipos y crear una clase de envío que se deriva de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Un objeto de esa clase tiene propiedades y operaciones que duplican las del objeto de servidor. La aplicación llama a operaciones y las propiedades de este objeto y funcionalidad que se hereda de `COleDispatchDriver` enruta estas llamadas al sistema OLE, que a su vez se enruta al objeto de servidor.  
  
 Si decide incluir automatización cuando se creó el proyecto, Visual C++ mantiene automáticamente este archivo de biblioteca de tipos para usted. Como parte de cada compilación, se generará el archivo .tlb mediante MkTypLib.  
  
### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Para crear una clase de envío de un archivo de biblioteca de tipos (.tlb)  
  
1.  En la vista de clases o en el Explorador de soluciones, haga clic en el proyecto y haga clic en **agregar** y, a continuación, haga clic en **Agregar clase** en el menú contextual.  
  
2.  En el **Agregar clase** cuadro de diálogo, seleccione la **Visual c++ / MFC** carpeta en el panel izquierdo. Seleccione el **clase MFC de TypeLib** icono desde el panel derecho, haga clic en **abiertos**.  
  
3.  En el **Asistente para agregar clases de la biblioteca de tipos** cuadro de diálogo, seleccione una biblioteca de tipos desde el **bibliotecas de tipos disponibles** lista desplegable. El **Interfaces** cuadro muestra las interfaces disponibles para la biblioteca de tipos seleccionada.  
  
    > [!NOTE]
    >  Puede seleccionar interfaces de más de una biblioteca de tipos.  
  
     Para seleccionar interfaces, haga doble clic en ellos o haga clic en el **agregar** botón. Cuando lo hace, los nombres de las clases de envíos aparecerán en el **clases generadas** cuadro. Puede editar los nombres de clase en la `Class` cuadro.  
  
     El **archivo** cuadro muestra el archivo en el que se declarará la clase. (puede modificar este nombre de archivo también). También puede usar el botón Examinar para seleccionar otros archivos, si prefiere tener la información de encabezado e implementación escrita en archivos existentes o en un directorio distinto del directorio del proyecto.  
  
    > [!NOTE]
    >  Todas las clases de envío para las interfaces seleccionadas se colocará en el archivo especificado aquí. Si desea que las interfaces que se declaren en encabezados independientes, debe ejecutar a este asistente para cada archivo de encabezado que se va a crear.  
  
    > [!NOTE]
    >  Alguna información de la biblioteca de tipos puede almacenarse en archivos con. ARCHIVO DLL. OCX, o. Extensiones de archivo OLB.  
  
4.  Haga clic en **Finalizar**.  
  
     El Asistente para, a continuación, escribirá el código para las clases de envío con los nombres de archivo y la clase especificada.  
  
## <a name="see-also"></a>Vea también  
 [Clientes de automatización](../mfc/automation-clients.md)

