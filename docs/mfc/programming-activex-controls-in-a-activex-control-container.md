---
title: 'Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bae926cfc7e83edeef9ee68c7ce7118c55009a08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355046"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX
En este artículo se describe el proceso para tener acceso a la expuesta [métodos](../mfc/mfc-activex-controls-methods.md) y [propiedades](../mfc/mfc-activex-controls-properties.md) de controles ActiveX incrustados. Básicamente, seguirá estos pasos:  
  
1.  [Insertar un control ActiveX en el proyecto de contenedor de ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) mediante la galería.  
  
2.  [Definir una variable miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (u otra forma de acceso) del mismo tipo como el ActiveX clase contenedora del control.  
  
3.  [Programar el control ActiveX](#_core_programming_the_activex_control) utilizando predefinidos las funciones miembro de la clase contenedora.  
  
 Para este análisis, supone que ha creado un proyecto basado en el cuadro de diálogo (denominado Container) compatible con controles ActiveX. El control del ejemplo, Circ, se agregará al proyecto resultante.  
  
 Una vez que el control Circ se inserta en el proyecto (paso 1), inserte una instancia del control Circ en el cuadro de diálogo principal de la aplicación.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Para agregar el control Circ a la plantilla de cuadro de diálogo  
  
1.  Cargar el proyecto de contenedor de controles ActiveX. En este ejemplo, utilice el `Container` proyecto.  
  
2.  Haga clic en la ficha Vista de recursos.  
  
3.  Abra la **diálogo** carpeta.  
  
4.  Haga doble clic en la plantilla de cuadro de diálogo principal. En este ejemplo, utilice **IDD_CONTAINER_DIALOG**.  
  
5.  Haga clic en el icono del control Circ en el cuadro de herramientas.  
  
6.  Haga clic en una zona en el cuadro de diálogo para insertar el control Circ.  
  
7.  Desde el **archivo** menú, elija **guardar todo** para guardar todas las modificaciones en la plantilla de cuadro de diálogo.  
  
## <a name="modifications-to-the-project"></a>Modificaciones en el proyecto  
 Para habilitar la aplicación contenedora tener acceso al control Circ, Visual C++ agrega automáticamente la clase contenedora (`CCirc`) el archivo de implementación (. CPP) para el proyecto de contenedor y el archivo de encabezado (. (H) del archivo para el archivo de encabezado del cuadro de diálogo:  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a> El archivo de encabezado (. (H) archivo  
 Para obtener y establecer propiedades (e invocar métodos) para el control Circ, la `CCirc` clase contenedora proporciona una declaración de todas se exponen métodos y propiedades. En el ejemplo, estas declaraciones se encuentran en CIRC. H. El ejemplo siguiente es la parte de la clase `CCirc` que define las interfaces expuestas del control ActiveX:  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 A continuación, puede llamar a estas funciones de otros procedimientos de la aplicación utilizando la sintaxis de C++ normal. Para obtener más información sobre el uso de esta función miembro configurada para obtener acceso a los métodos y propiedades del control, vea la sección [programación del control ActiveX](#_core_programming_the_activex_control).  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a> Modificaciones de variables de miembro para el proyecto  
 Una vez que el control ActiveX se ha agregado al proyecto e incrustado en un contenedor de cuadro de diálogo, puede tener acceso por otras partes del proyecto. Es la manera más fácil de obtener acceso al control [crear una variable de miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) de la clase de cuadro de diálogo, `CContainerDlg` (paso 2), que es el mismo tipo que la clase contenedora que se agrega al proyecto por Visual C++. A continuación, puede utilizar la variable miembro para tener acceso al control incrustado en cualquier momento.  
  
 Cuando el **agregar variables miembro** cuadro de diálogo agrega el `m_circctl` miembro variable al proyecto, también agrega las siguientes líneas al archivo de encabezado (. (H) de la `CContainerDlg` clase:  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 Además, una llamada a **DDX_Control** se agrega automáticamente a la `CContainerDlg`de implementación de `DoDataExchange`:  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a> Programar el Control ActiveX  
 En este momento, ha insertado el control ActiveX en la plantilla de cuadro de diálogo y cree una variable miembro para ella. Ahora puede usar la sintaxis común de C++ para tener acceso a las propiedades y métodos del control incrustado.  
  
 Como se indicó (en [el archivo de encabezado (. (H) del archivo](#_core_the_wrapper_class_header_28h29_file)), el archivo de encabezado (. (H) para la `CCirc` clase contenedora, en este caso CIRC. H, contiene una lista de funciones miembro que pueden utilizar para obtener y establecer cualquier valor de propiedad expuesta. También existen funciones de miembro para los métodos expuestos.  
  
 Es un lugar común para modificar las propiedades del control en el `OnInitDialog` función miembro de la clase de cuadro de diálogo principal. Esta función se invoca justo antes de que el cuadro de diálogo aparece y se utiliza para inicializar su contenido, incluido cualquiera de sus controles.  
  
 El siguiente ejemplo de código utiliza el `m_circctl` variable miembro para modificar las propiedades Caption y CircleShape del control Circ incrustado:  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

