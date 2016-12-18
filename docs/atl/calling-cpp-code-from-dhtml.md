---
title: "Calling C++ Code from DHTML | Microsoft Docs"
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
  - "DHTML, calling C++ code from"
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Calling C++ Code from DHTML
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control DHTML puede hospedarse en un contenedor, como contenedor de prueba o Internet Explorer.  Vea [Propiedades y eventos de pruebas con el contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo tener acceso al contenedor de prueba.  
  
 El contenedor que hospeda el control se comunica con el control mediante interfaces de control normales.  Se utiliza la interfaz de envío que finaliza con “la interfaz de usuario” para comunicarse con su C\+\+ codifican y el recurso de HTML.  En [Modificación de Control ATL DHTML](../atl/modifying-the-atl-dhtml-control.md), puede practicar la adición de los métodos que se utilizarán por estas interfaces diferentes.  
  
 Para ver un ejemplo de llamada a C\+\+ codificadas de DHTML, de [cree un control DHTML](../atl/creating-an-atl-dhtml-control.md) mediante el asistente para controles ATL y examinar el código en el archivo de encabezado y en el archivo HTML.  
  
## Declarar los métodos WebBrowser en el archivo de encabezado  
 Para invocar métodos de C\+\+ de la interfaz de usuario de DHTML, debe agregar métodos a la interfaz de la interfaz de usuario del control.  Por ejemplo, el archivo de encabezado creado por el asistente para controles ATL contiene el método `OnClick`de C\+\+, que es un miembro de la interfaz de la interfaz de usuario del control asistente\- generado.  
  
 Examine `OnClick` en el archivo de .h de control:  
  
 [!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/CPP/calling-cpp-code-from-dhtml_1.h)]  
  
 El primer parámetro, `pdispBody`, es un puntero a la interfaz de envío del objeto de cuerpo.  El segundo parámetro, `varColor`, identifica color para aplicar al control.  
  
## Llamada C\+\+ codificada en el archivo HTML  
 Una vez que se ha declarado los métodos WebBrowser en el archivo de encabezado, puede llamar a los métodos del archivo HTML.  Observe en el archivo HTML que las inserciones del asistente para controles ATL tres métodos de envío de Windows: tres métodos de `OnClick` enviando mensajes para cambiar el color de fondo del control.  
  
 Examine uno de los métodos en el archivo HTML:  
  
 `<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`  
  
 En el código HTML anterior, el método externo de la ventana, `OnClick`, se le llama como parte del botón.  El método tiene dos parámetros: `theBody`, que hace referencia el cuerpo del documento HTML, y `"red"`, que indica que el color de fondo del control se convertirá en rojo cuando se hace clic en el botón.  `Red` que sigue la etiqueta es la etiqueta del botón.  
  
 Vea [Modificación de Control ATL DHTML](../atl/modifying-the-atl-dhtml-control.md) para obtener más información sobre cómo incluir sus propios métodos.  Vea [Identificar los elementos de proyecto de control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) para obtener más información sobre el archivo HTML.  
  
## Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)