---
title: "Colocar el Control en una página Web (ATL Tutorial, parte 7) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6990539ca6f0bc2956822547e3d41c00c841caf8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Colocar el control en una página web (Tutorial de ATL, Parte 7)
El control ya está terminado. Para ver el control de trabajo en una situación real, colóquelo en una página Web. Se creó un archivo HTML que contiene el control cuando se define el control. Abra el archivo PolyCtl.htm desde **el Explorador de soluciones**, y puede ver el control en una página Web.  
  
 En este paso, se script la página Web para responder a eventos. Además, modificará el control para que Internet Explorer sepa que el control es seguro para scripting.  
  
## <a name="scripting-the-web-page"></a>Secuencias de comandos de la página Web  
 El control no hace nada aún, por lo que cambiar la página Web para responder a los eventos que se envían.  
  
#### <a name="to-script-the-web-page"></a>En la página Web de la secuencia de comandos  
  
1.  Abra PolyCtl.htm y seleccione la vista HTML. Agregue las siguientes líneas en el código HTML. Se debe agregar después `</OBJECT>` pero antes `</BODY>`.  
  
 ```  
 
 <SCRIPT LANGUAGE="VBScript">  
 <!--  
    Sub PolyCtl_ClickIn(x, y)  
    PolyCtl.Sides = PolyCtl.Sides + 1  
    End Sub  
    Sub PolyCtl_ClickOut(x, y)  
    PolyCtl.Sides = PolyCtl.Sides - 1  
    End Sub  
 -->  
 </SCRIPT>  
 ```  
  
2.  Guarde el archivo HTM.  
  
 Ha agregado código VBScript que obtiene la propiedad de los lados del control y aumenta el número de caras en uno si hace clic dentro del control. Si hace clic fuera del control, reduzca el número de lados en uno.  
  
## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Que indica que el Control es seguro para Scripting  
 Puede ver la página Web con el control en el Explorador de Internet, o bien, utilizar más para su comodidad, la vista de explorador Web integrada en Visual C++. Para ver el control en la vista de explorador Web, haga clic en PolyCtl.htm y haga clic en **ver en el explorador**.  
  
 En función de la configuración de seguridad actual de Internet Explorer, es posible que reciba una alerta de seguridad de diálogo cuadro que indica que el control no puede ser seguro para la ejecución del script y podría provocar daños. Por ejemplo, si tiene un control que muestra un archivo, pero también tenía un `Delete` método que elimina un archivo, sería seguro si sólo lo ve en una página. No sería seguro generar un script, sin embargo, dado que un usuario podría llamar a la `Delete` método.  
  
> [!IMPORTANT]
>  Para este tutorial, puede cambiar la configuración de seguridad de Internet Explorer para ejecutar los controles ActiveX no marcados como seguros. En el Panel de Control, haga clic en **propiedades de Internet** y haga clic en **seguridad** para cambiar la configuración apropiada. Cuando se haya completado el tutorial, cambie la configuración de seguridad a su estado original.  
  
 Mediante programación puede avisar Internet Explorer que no es necesario mostrar el cuadro de diálogo de alerta de seguridad para este control particular. Para hacer esto con el `IObjectSafety` interfaz y ATL proporciona una implementación de esta interfaz en la clase [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Para agregar la interfaz al control, agregue `IObjectSafetyImpl` a la lista de las clases heredadas y agregar una entrada para él en el mapa COM.  
  
#### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Para agregar IObjectSafetyImpl al control  
  
1.  Agregue la siguiente línea al final de la lista de clases heredadas en PolyCtl.h y agregue una coma a la línea anterior:  
  
 [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  Agregue la siguiente línea al mapa COM en PolyCtl.h:  
  
 [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## <a name="building-and-testing-the-control"></a>Compilar y probar el control  
 Compilar el control. Una vez que haya finalizado la compilación, abra de nuevo PolyCtl.htm en la vista de explorador. Esta vez, debe mostrarse la página Web directamente, sin el cuadro de diálogo Alerta de seguridad. Haga clic dentro del polígono; el número de lados aumenta en uno. Haga clic fuera del polígono para reducir el número de lados. Si intenta reducir el número de lados por debajo de tres, verá el mensaje de error que se establece.  
  
 [Vuelva al paso 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="next-steps"></a>Pasos siguientes  
 Esto concluye el tutorial ATL. Para obtener vínculos a más información acerca de ATL, vea el [página de inicio de ATL](../atl/active-template-library-atl-concepts.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)

