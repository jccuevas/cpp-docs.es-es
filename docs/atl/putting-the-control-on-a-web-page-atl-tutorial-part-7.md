---
title: "Colocar el control en una p&#225;gina web (Tutorial de ATL, Parte 7) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Colocar el control en una p&#225;gina web (Tutorial de ATL, Parte 7)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El control finaliza ahora.  Para ver el control en funcionamiento en una situación real, colóquelo en una página web.  Cuando se definió el control se creó un archivo HTML que contiene el control.  Abra el archivo PolyCtl.htm desde **Explorador de soluciones** y podrá ver el control en una página web.  
  
 En este paso, generará script en la página web para responder a eventos.  También modificará el control para que Internet Explorer sepa que el control es seguro para la creación de script.  
  
## Scripting de la página web  
 El control no realiza ninguna función aún, así que cambie la página web para responder a los eventos que envía.  
  
#### Para crear un script de la página web  
  
1.  Abra PolyCtl.htm y seleccione la vista HTML.  Agregue las líneas siguientes al código HTML.  Deben agregarse después de `</OBJECT>`, pero antes de `</BODY>`.  
  
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
  
 Ha agregado algún código de VBScript que obtiene la propiedad Sides del control e incrementa el número de lados en uno si hace clic dentro del control.  Si hace clic fuera del control, reducirá el número de lados por uno.  
  
## Lo que indica que el control es seguro para la creación de scripts  
 Puede ver la página web con el control en Internet Explorer o, de un modo más conveniente, usar la vista de explorador web incluida en Visual C\+\+.  Para ver el control en la vista de explorador web, haga clic con el botón secundario en PolyCtl.htm y haga clic en **Ver en el explorador**.  
  
 Sobre la base de la configuración de seguridad actual de Internet Explorer, puede que reciba un cuadro de diálogo de alerta de seguridad que indica que el control quizá no sea seguro para el script y pueda causar daños.  Por ejemplo, si tiene un control que muestra un archivo pero también tiene un método `Delete` que eliminó un archivo, sería seguro si lo acaba de ver en una página.  Sería no seguro generar script, sin embargo, porque alguien podría llamar al método `Delete`.  
  
> [!IMPORTANT]
>  En este tutorial, puede cambiar la configuración de seguridad de Internet Explorer para ejecutar los controles ActiveX que no estén marcadas como seguros.  En el Panel de control, haga clic en **Propiedades de Internet** y en **Seguridad** para cambiar los valores adecuados.  Tras completar el tutorial, cambie la configuración de seguridad a su estado original.  
  
 Mediante programación puede alertar a Internet Explorer, que no necesita mostrar el cuadro de diálogo Alerta de seguridad para este control determinado.  Puede hacerlo mediante la interfaz `IObjectSafety` y ATL proporciona una implementación de esta interfaz en la clase [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md).  Para agregar la interfaz al control, agregue `IObjectSafetyImpl` a la lista de clases heredadas y agregue una entrada para ella en el mapa COM.  
  
#### Para agregar IObjectSafetyImpl al control  
  
1.  Agregue la siguiente línea al final de la lista de clases heredadas en PolyCtl.h y agregue una coma a la línea anterior:  
  
     [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/CPP/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  Agregue la siguiente línea al mapa COM de PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/CPP/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## Compilar y probar el control  
 Crear el control.  Una vez finalizada la compilación, abra de nuevo PolyCtl.htm en vista de explorador.  Esta vez, la página web se debe mostrar directamente sin el cuadro de diálogo de alerta de seguridad.  Haga clic dentro del polígono; el número de lados se incrementa por uno.  Haga clic fuera del polígono para reducir el número de lados.  Si intenta reducir el número de lados por debajo de tres, verá el mensaje de error que estableció.  
  
 [Volvamos al paso 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## Pasos siguientes  
 Esto concluye el tutorial de ATL.  Para obtener vínculos a más información sobre ATL, vea [página de inicio de ATL](../atl/active-template-library-atl-concepts.md).  
  
## Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)