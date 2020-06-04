---
title: Colocar el control en una página web (Tutorial de ATL, Parte 7)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
ms.openlocfilehash: db6dcc57ff9f3748d802e76617ef18dea8f9506c
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344359"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Colocar el control en una página web (Tutorial de ATL, Parte 7)

El control ya está completado. Para ver el control funcione en una situación real, colóquelo en una página Web. Un archivo HTML que contiene el control se creó al definir el control. Abra el archivo PolyCtl.htm desde **el Explorador de soluciones**, y puede ver el control en una página Web.

En este paso, agregar funcionalidad al control y la página Web para responder a eventos de script. También modificará el control para que Internet Explorer sepa que el control es seguro para scripting.

## <a name="adding-new-functionality"></a>Agregar nueva funcionalidad

### <a name="to-add-control-features"></a>Para agregar las características de control

1. Abra PolyCtl.cpp y reemplace el código siguiente:

    ```cpp
    if (PtInRegion(hRgn, xPos, yPos))
        Fire_ClickIn(xPos, yPos);
    else
        Fire_ClickOut(xPos, yPos);
    ```

    with

    ```cpp
    short temp = m_nSides;
    if (PtInRegion(hRgn, xPos, yPos))
    {
        Fire_ClickIn(xPos, yPos);
        put_Sides(++temp);
    }
    else
    {
        Fire_ClickOut(xPos, yPos);
        put_Sides(--temp);
    }
    ```

La forma ahora agregará o quitará lados según donde se hizo clic.

## <a name="scripting-the-web-page"></a>Secuencias de comandos de la página Web

El control no hace nada aún, así que cambie la página Web para responder a los eventos que se envían.

### <a name="to-script-the-web-page"></a>En el script de la página Web

1. Abra PolyCtl.htm y seleccione la vista HTML. Agregue las líneas siguientes al código HTML. Deben agregarse después `</OBJECT>` pero antes `</BODY>`.

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - adding side")
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - removing side")
        End Sub
    -->
    </SCRIPT>
    ```

1. Guarde el archivo HTM.

Ha agregado algún código VBScript que obtiene la propiedad Sides del control. Aumenta el número de lados por uno si hace clic dentro del control. Si hace clic fuera del control, reduzca el número de lados por uno.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Que indica que el Control es seguro para Scripting

Sólo puede ver la página Web con el control de Internet Explorer. Otros exploradores ya no admiten controles ActiveX debido a vulnerabilidades de seguridad.

> [!NOTE]
> Si el control no está visible, sabe que algunos exploradores necesitan ajustes de configuración para ejecutar los controles ActiveX. Consulte la documentación del explorador sobre cómo habilitar los controles ActiveX.

Según la configuración actual de seguridad de Internet Explorer, puede aparecer un cuadro de diálogo de alerta de seguridad. Indica que el control puede no ser seguro para el script y pueda causar daños. Por ejemplo, si tiene un control que muestra un archivo, pero también tenía un `Delete` método que se eliminó un archivo, sería seguro si lo acaba de ver en una página. No sería seguro generar un script, sin embargo, dado que alguien podría llamar a la `Delete` método.

> [!IMPORTANT]
> Para este tutorial, puede cambiar la configuración de seguridad de Internet Explorer para ejecutar los controles ActiveX que no están marcados como seguros. En el Panel de Control, haga clic en **propiedades de Internet** y haga clic en **seguridad** para cambiar la configuración adecuada. Cuando haya completado el tutorial, cambie la configuración de seguridad a su estado original.

Mediante programación puede alertar Internet Explorer que no es necesario mostrar el cuadro de diálogo de alerta de seguridad para este control particular. Puede hacerlo mediante el uso de la `IObjectSafety` interfaz. ATL proporciona una implementación de esta interfaz en la clase [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Para agregar la interfaz al control, agregue `IObjectSafetyImpl` a la lista de clases heredadas y agregue una entrada para él en el mapa COM.

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Para agregar IObjectSafetyImpl al control

1. Agregue la siguiente línea al final de la lista de clases heredadas en PolyCtl.h y agregue una coma a la línea anterior:

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. Agregue la siguiente línea al mapa COM de PolyCtl.h:

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>Compilar y probar el control

Compilar el control. Una vez finalizada la compilación, abra de nuevo PolyCtl.htm en vista de explorador. Esta vez, la página Web se debe mostrar directamente sin el **alerta de seguridad** cuadro de diálogo. Si hace clic dentro del polígono, aumenta el número de lados en uno. Haga clic fuera del polígono para reducir el número de lados.

[Vuelva al paso 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>Pasos siguientes

Este paso finaliza el tutorial ATL. Para obtener vínculos para obtener más información sobre ATL, vea el [página de inicio de ATL](../atl/active-template-library-atl-concepts.md).

## <a name="see-also"></a>Vea también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
