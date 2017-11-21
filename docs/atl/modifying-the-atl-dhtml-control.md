---
title: Modificar el Control DHTML ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 74ed32c0322d23cd3da1d439dcc8d8eadb246c13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="modifying-the-atl-dhtml-control"></a>Modificar el Control DHTML ATL
El Asistente para controles ATL proporciona código de inicio para que pueda compilar y ejecutar el control, por lo que puede ver cómo los métodos se escriben en los archivos de proyecto y cómo DHTML llama a código de C++ del control mediante los métodos de envío. Puede agregar cualquier método de envío a la interfaz. A continuación, puede llamar a los métodos en el recurso HTML.  
  
#### <a name="to-modify-the-atl-dhtml-control"></a>Para modificar el control DHTML ATL  
  
1.  En la vista de clases, expanda el proyecto de control.  
  
     Tenga en cuenta que la interfaz que termina en "UI" tiene un método, `OnClick`. La interfaz que no termina en "UI" no tiene ningún método.  
  
2.  Agregue un método denominado `MethodInvoked` a la interfaz que no termina en "UI".  
  
     Este método se agregarán a la interfaz que se utiliza en el contenedor del control para la interacción de contenedor, no a la interfaz utilizada por el código DHTML para interactuar con el control. Solo el contenedor puede invocar este método.  
  
3.  Busque el método auxiliar en el archivo .cpp y agregue código para mostrar un cuadro de mensaje, por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  Agregue otro método llamado `HelloHTML`, pero esta vez, agregar a la interfaz que termina en "UI". Buscar la escalada con stub `HelloHTML` método en el .cpp archivo y agregar código para mostrar un cuadro de mensaje, por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  Agregue un tercer método `GoToURL`, a la interfaz que no termina en "UI". Implemente este método mediante una llamada a [IWebBrowser2:: Navigate](https://msdn.microsoft.com/library/aa752133.aspx), como se indica a continuación:  
  
 [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]  
  
     Puede usar el **IWebBrowser2** métodos porque ATL proporciona un puntero a esa interfaz en el archivo .h.  
  
 A continuación, modifique el recurso HTML para invocar los métodos que se ha creado. Agregará tres botones para llamar a estos métodos.  
  
#### <a name="to-modify-the-html-resource"></a>Para modificar el recurso HTML  
  
1.  En el Explorador de soluciones, haga doble clic en el archivo .htm para mostrar el recurso HTML.  
  
     Examine el código HTML, especialmente las llamadas a los métodos de envío externos de Windows. El código HTML llama el proyecto `OnClick` método y los parámetros indican el cuerpo del control (`theBody`) y el color que desea asignar ("`red`"). El texto que sigue a la llamada al método es la etiqueta que aparece en el botón.  
  
2.  Agregue otro `OnClick` método, solo cambiar el color. Por ejemplo:  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
 ```  
  
     Este método creará un botón, etiquetado **actualizar**, que el usuario puede hacer clic para devolver el control al fondo blanco, original.  
  
3.  Agregue la llamada a la `HelloHTML` método que creó. Por ejemplo:  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
 ```  
  
     Este método creará un botón, etiquetado **HelloHTML**, que el usuario puede hacer clic para mostrar la `HelloHTML` cuadro de mensaje.  
  
 Ahora puede compilar y [probar el control DHTML modificado](../atl/testing-the-modified-atl-dhtml-control.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)

