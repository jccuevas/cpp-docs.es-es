---
title: 'Los clientes de automatización: Usar bibliotecas de tipos | Microsoft Docs'
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
ms.openlocfilehash: 3899fd61426e9b07294f624f7f3ce68c2acc002b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198651"
---
# <a name="automation-clients-using-type-libraries"></a>Clientes de Automation: Usar bibliotecas de tipos
Los clientes de automatización deben tener información sobre las propiedades y métodos de objetos de servidor si los clientes son manipular objetos de los servidores. Las propiedades tienen tipos de datos; a menudo, los métodos devuelven valores y aceptan parámetros. El cliente requiere información sobre los tipos de datos de todos ellos para poder enlazar estáticamente con el tipo de objeto de servidor.  
  
 Se pueden hacer esta información de tipos conocida de varias maneras. La manera recomendada es crear una biblioteca de tipos.  
  
 Para obtener información sobre [MkTypLib](/windows/desktop/Midl/differences-between-midl-and-mktyplib), consulte el SDK de Windows.  
  
 Visual C++ puede leer un archivo de biblioteca de tipos y crear una clase de envío derivada [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Un objeto de esa clase tiene propiedades y operaciones que duplican los del objeto de servidor. La aplicación llama a las propiedades y operaciones de este objeto y la funcionalidad heredada de `COleDispatchDriver` enruta estas llamadas al sistema OLE, que a su vez las enruta al objeto de servidor.  
  
 Si decide incluir automatización cuando se creó el proyecto, Visual C++ mantiene automáticamente este archivo de biblioteca de tipos para usted. Como parte de cada compilación, se generará el archivo .tlb con MkTypLib.  
  
### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Para crear una clase de envío de un archivo de biblioteca de tipos (.tlb)  
  
1.  En la vista de clases o en el Explorador de soluciones, haga clic en el proyecto y haga clic en **agregar** y, a continuación, haga clic en **Agregar clase** en el menú contextual.  
  
2.  En el **Agregar clase** cuadro de diálogo, seleccione el **c++ de Visual c++ / MFC** carpeta en el panel izquierdo. Seleccione el **clase MFC de TypeLib** icono en el panel derecho, haga clic en **abierto**.  
  
3.  En el **Asistente para agregar clases de la biblioteca de tipos** cuadro de diálogo, seleccione una biblioteca de tipos desde el **bibliotecas de tipos disponibles** lista desplegable. El **Interfaces** cuadro muestra las interfaces disponibles para la biblioteca de tipos seleccionada.  
  
    > [!NOTE]
    >  Puede seleccionar las interfaces de más de una biblioteca de tipos.  
  
     Seleccionar interfaces, haga doble clic en ellos o haga clic en el **agregar** botón. Al hacerlo, los nombres de las clases de envíos aparecerá en el **clases generadas** cuadro. Puede editar los nombres de clase en el `Class` cuadro.  
  
     El **archivo** cuadro muestra el archivo en el que se declarará la clase. (puede editar este nombre de archivo también). También puede usar el botón Examinar para seleccionar otros archivos, si prefiere tener la información de encabezado e implementación escrita en archivos existentes o en un directorio distinto al proyecto.  
  
    > [!NOTE]
    >  Todas las clases de distribución de las interfaces seleccionadas se colocará en el archivo especificado aquí. Si desea que las interfaces que se declararan en encabezados independientes, debe ejecutar a este asistente para cada archivo de encabezado que desea crear.  
  
    > [!NOTE]
    >  Alguna información de la biblioteca de tipos puede almacenarse en archivos con. ARCHIVO DLL. OCX, o. Extensiones de archivo OLB.  
  
4.  Haga clic en **Finalizar**.  
  
     El asistente, a continuación, escribirá el código para las clases de envío mediante la clase especificada y los nombres de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Clientes de automatización](../mfc/automation-clients.md)

