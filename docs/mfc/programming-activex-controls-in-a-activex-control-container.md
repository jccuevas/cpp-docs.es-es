---
title: "Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de controles ActiveX [C++], obtener acceso a controles ActiveX"
  - "contenedores de controles ActiveX [C++], clases contenedoras"
  - "controles ActiveX [C++], obtener acceso"
  - "controles ActiveX [C++], clases contenedoras"
  - "Confirmar clases (cuadro de diálogo)"
  - "archivos de encabezado [C++], para clase contenedora del control ActiveX"
  - "controles ActiveX en MFC [C++], obtener acceso en contenedores"
  - "clases contenedoras [C++], controles ActiveX"
  - "clases contenedoras [C++], utilizar"
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe el proceso para tener acceso a [métodos](../mfc/mfc-activex-controls-methods.md) expuesto y a [propiedades](../mfc/mfc-activex-controls-properties.md) de controles ActiveX incrustados.  Básicamente, debe seguir estos pasos:  
  
1.  [Inserte un control ActiveX en el proyecto de contenedor ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) mediante galería.  
  
2.  el[Defina una variable miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) \(u otro formulario de acceso\) del mismo tipo que la clase contenedora de controles ActiveX.  
  
3.  [Programar el control ActiveX](#_core_programming_the_activex_control) mediante las funciones predefinidas de miembro de la clase contenedora.  
  
 Para este tutorial, supongamos que ha creado un proyecto diálogo\- basado \(denominado Container\) con el control ActiveX.  El ejemplo de Circ, Circ, se agregará al proyecto resultante.  
  
 Una vez que el control de Circ se inserta en el proyecto \(el paso 1\), inserta una instancia del control de Circ en el cuadro de diálogo principal de la aplicación.  
  
## Procedimientos  
  
#### Para agregar el control de Circ a la plantilla de cuadro de diálogo  
  
1.  Cargue el proyecto de contenedor de controles ActiveX.  En este ejemplo, use el proyecto de `Container` .  
  
2.  Haga clic en la ficha Vista de recursos.  
  
3.  Abra la carpeta de **Cuadro de diálogo** .  
  
4.  Haga doble clic en la plantilla principal del cuadro de diálogo.  En este ejemplo, use **IDD\_CONTAINER\_DIALOG**.  
  
5.  Haga clic en el icono de control de Circ en el cuadro de herramientas.  
  
6.  Haga clic en un punto dentro del cuadro de diálogo para incrustar el control de Circ.  
  
7.  En el menú de **archivo** , elija **guardar todo** para guardar todas las modificaciones a la plantilla en el cuadro de diálogo.  
  
## Modificaciones al proyecto  
 Para habilitar la aplicación contenedora para tener acceso al control de Circ, Visual C\+\+ agrega automáticamente el archivo de implementación de la clase contenedora \(`CCirc`\) \(.CPP\) al proyecto del contenedor y el encabezado de la clase contenedora \(. H\) archivo al archivo de encabezado de cuadro de diálogo:  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a> El encabezado de la clase contenedora \(. H\) archivo  
 Para obtener y establecer propiedades \(e invocar métodos\) para el control de Circ, la clase contenedora de `CCirc` proporciona una declaración de todos los métodos y propiedades expuestos.  En el ejemplo, estas declaraciones se encuentran en CIRC.H.  El ejemplo siguiente forma parte de la clase `CCirc` que define las interfaces expuestas del control ActiveX:  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 Estas funciones se pueden llamar desde otro de los procedimientos de la aplicación mediante la sintaxis normal de C\+\+.  Para obtener más información sobre cómo usar este conjunto de funciones de miembro para tener acceso a los métodos y propiedades de control, vea la sección [Programar el control ActiveX](#_core_programming_the_activex_control).  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a> Variable miembro Modifications al proyecto  
 Una vez que el control ActiveX se ha agregado al proyecto y se ha insertado en un contenedor del cuadro de diálogo, puede obtener acceso a otras partes del proyecto.  La manera más fácil de tener acceso al control a [cree una variable miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) de la clase de diálogo, `CContainerDlg` \(el paso 2\), con el mismo tipo que la clase contenedora agregará al proyecto en Visual C\+\+.  Puede utilizar a la variable miembro para obtener acceso al control incrustado en cualquier momento.  
  
 Cuando el cuadro de diálogo de **Agregar variable de miembro** agrega a la variable miembro de `m_circctl` al proyecto, también agrega las líneas siguientes al archivo de encabezado \(. H\) de la clase de `CContainerDlg` :  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 Además, una llamada a **DDX\_Control** se agrega automáticamente a la implementación de `CContainerDlg` de `DoDataExchange`:  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a> Programar el control ActiveX  
 En este punto, ha insertado el control ActiveX en la plantilla de cuadro de diálogo y ha creado una variable miembro para él.  Ahora puede utilizar la sintaxis habitual de C\+\+ para tener acceso a las propiedades y los métodos de control incrustado.  
  
 Como conocido \(en [El encabezado de la clase contenedora \(. H\) archivo](#_core_the_wrapper_class_header_28h29_file)\), el archivo de encabezado \(. H\) para la clase contenedora de `CCirc` , en este caso CIRC.H, contiene una lista de funciones miembro que puede utilizar para obtener y establecer los valores de propiedad expuesta.  Las funciones miembro para los métodos expuestos también están disponibles.  
  
 Un lugar común para modificar las propiedades del control es la función miembro de `OnInitDialog` de la clase principal del diálogo.  Esta función se denomina justo antes del cuadro de diálogo y se utiliza para inicializar su contenido, incluso a ninguno de los controles.  
  
 El ejemplo de código siguiente utiliza la variable miembro de `m_circctl` para modificar las propiedades caption y de CircleShape de control incrustado de Circ:  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)