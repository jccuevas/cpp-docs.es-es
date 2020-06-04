---
title: 'Clientes de Automation: Usar bibliotecas de tipos'
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
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
ms.openlocfilehash: 480f8fca46b13d445f372311ed837475c71a1e9d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509223"
---
# <a name="automation-clients-using-type-libraries"></a>Clientes de Automation: Usar bibliotecas de tipos

Los clientes de automatización deben tener información acerca de las propiedades y los métodos de los objetos de servidor si los clientes van a manipular los objetos de los servidores. Las propiedades tienen tipos de datos; a menudo, los métodos devuelven valores y aceptan parámetros. El cliente requiere información sobre los tipos de datos de todos ellos para enlazar estáticamente con el tipo de objeto de servidor.

Esta información de tipo puede hacerse conocida de varias maneras. La manera recomendada es crear una biblioteca de tipos.

Para obtener información sobre [MkTypLib](/windows/win32/Midl/differences-between-midl-and-mktyplib), vea el Windows SDK.

Visual C++ puede leer un archivo de biblioteca de tipos y crear una clase de envío derivada de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Un objeto de esa clase tiene propiedades y operaciones que duplican las del objeto de servidor. La aplicación llama a las propiedades y operaciones de este objeto y la funcionalidad `COleDispatchDriver` heredada de enruta estas llamadas al sistema OLE, que a su vez las enruta al objeto de servidor.

Visual C++ automáticamente mantiene este archivo de biblioteca de tipos si decide incluir la automatización cuando se creó el proyecto. Como parte de cada compilación, el archivo. tlb se generará con MkTypLib.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Para crear una clase de envío a partir de un archivo de biblioteca de tipos (. tlb)

1. En Vista de clases o Explorador de soluciones, haga clic con el botón secundario en el proyecto, haga clic en **Agregar** y, a continuación, haga clic en **Agregar clase** en el menú contextual.

1. En el cuadro de diálogo **Agregar clase** , seleccione la carpeta **Visual C++/MFC** en el panel izquierdo. Seleccione el icono **clase MFC de typelib** en el panel derecho y haga clic en **abrir**.

1. En el cuadro de diálogo **Asistente para agregar clases de la biblioteca** de tipos, seleccione una biblioteca de tipos en la lista desplegable **bibliotecas de tipos disponibles** . El cuadro **interfaces** muestra las interfaces disponibles para la biblioteca de tipos seleccionada.

    > [!NOTE]
    >  Puede seleccionar interfaces de más de una biblioteca de tipos.

   Para seleccionar interfaces, haga doble clic en ellas o haga clic en el botón **Agregar** . Al hacerlo, los nombres de las clases de envío aparecerán en el cuadro **clases generadas** . Puede editar los nombres de clase en el `Class` cuadro.

   El cuadro **archivo** muestra el archivo en el que se declarará la clase. (también puede editar este nombre de archivo). También puede usar el botón Examinar para seleccionar otros archivos, si prefiere que la información de encabezado y de implementación se escriba en archivos existentes o en un directorio distinto del directorio del proyecto.

    > [!NOTE]
    >  Todas las clases de distribución de las interfaces seleccionadas se colocarán en el archivo especificado aquí. Si desea que las interfaces se declaren en encabezados independientes, debe ejecutar este asistente para cada archivo de encabezado que desee crear.

    > [!NOTE]
    >  Algunos datos de la biblioteca de tipos se pueden almacenar en archivos con. DLL,. OCX, o. OLB.

1. Haga clic en **Finalizar**

   A continuación, el asistente escribirá el código de las clases de envío con la clase y los nombres de archivo especificados.

## <a name="see-also"></a>Vea también

[Clientes de automatización](../mfc/automation-clients.md)
