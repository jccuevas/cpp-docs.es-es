---
title: "Modifying the ATL DHTML Control | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DHTML controls"
  - "DHTML controls, modificar"
  - "controles HTML, modificar"
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Modifying the ATL DHTML Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El asistente para controles ATL proporciona código inicial de modo que puede compilar y ejecutar el control, lo que puede ver cómo los métodos se escriben en los archivos de proyecto y cómo las llamadas de DHTML en el código de C\+\+ del control mediante los métodos send.  Puede agregar cualquier método de envío a la interfaz.  A continuación, puede llamar a los métodos en el recurso de HTML.  
  
#### Para modificar el control ATL DHTML  
  
1.  En la vista de clases, expanda el proyecto de control.  
  
     Observe que la interfaz que termina en “interfaz de usuario” tiene un método, `OnClick`.  Interfaz que no termina en “interfaz de usuario” no tiene métodos.  
  
2.  Agregue un método denominado `MethodInvoked`a la interfaz que no termina en “interfaz de usuario”.  
  
     Este método se agregará a la interfaz que se utiliza en el contenedor del control para la interacción con el contenedor, no a la interfaz utilizada por DHTML para interactuar con el control.  Sólo el contenedor puede invocar este método.  
  
3.  Busque el método tropezado\-hacia estuviera en el archivo .cpp y agregue el código para mostrar un cuadro de mensaje, por ejemplo:  
  
     [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  Agregue otro método denominado `HelloHTML`, sólo esta vez, lo agrega a la interfaz que termina en “interfaz de usuario”. Busque el método tropezado\-hacia fuera de `HelloHTML` en el archivo .cpp y agregue el código para mostrar un cuadro de mensaje, por ejemplo:  
  
     [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  Agregue un tercer método, `GoToURL`, interfaz que no termina en “interfaz de usuario”. Implemente este método llamando a [IWebBrowser2:: Navegar](https://msdn.microsoft.com/en-us/library/aa752133.aspx), como sigue:  
  
     [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_3.cpp)]  
  
     Puede utilizar los métodos de **IWebBrowser2** porque ATL proporciona un puntero a la interfaz en el archivo .h.  
  
 A continuación, modifique el recurso de HTML para invocar métodos que creó.  Agregará tres botones para invocar estos métodos.  
  
#### Para modificar el recurso HTML  
  
1.  En el explorador de soluciones, haga doble clic en el archivo .htm para mostrar el recurso de HTML.  
  
     Examine HTML, especialmente las llamadas a métodos externos de envío de Windows.  HTML llama al método de `OnClick` de proyecto, y los parámetros indican el cuerpo del control \(`theBody`\) y color a la asignación \(“`red`"\).  El texto que sigue a la llamada al método es la etiqueta que aparece en el botón.  
  
2.  agregue otro método de `OnClick` , sólo cambio color.  Por ejemplo:  
  
    ```  
    <br>  
    <br>  
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
    ```  
  
     Este método creará un botón, con la etiqueta **Actualizar**, que el usuario puede hacer clic para devolver el control al fondo original, blanco.  
  
3.  Agregue la llamada al método de `HelloHTML` que creó.  Por ejemplo:  
  
    ```  
    <br>  
    <br>  
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
    ```  
  
     Este método creará un botón, con la etiqueta **HelloHTML**, que el usuario puede hacer clic para mostrar el cuadro de mensaje de `HelloHTML` .  
  
 Ahora puede compilar y [probar el control modificado DHTML](../atl/testing-the-modified-atl-dhtml-control.md).  
  
## Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)