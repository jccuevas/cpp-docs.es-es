---
title: Agregar un evento (Tutorial de ATL, Parte 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: c9a7c6f38a2f47ec808081e440a200737ad1928a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127579"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Agregar un evento (Tutorial de ATL, Parte 5)

En este paso, agregará un `ClickIn` y un evento de `ClickOut` al control ATL. Desencadenará el evento `ClickIn` si el usuario hace clic en el polígono y activa `ClickOut` si el usuario hace clic fuera. Las tareas para agregar un evento son las siguientes:

- Agregar los métodos `ClickIn` y `ClickOut`

- Generar la biblioteca de tipos

- Implementar las interfaces de punto de conexión

## <a name="adding-the-clickin-and-clickout-methods"></a>Agregar los métodos Clickism y ClickOut

Cuando creó el control ATL en el paso 2, activó la casilla **puntos de conexión** . Esto creó la interfaz `_IPolyCtlEvents` en el archivo Polygon. idl. Tenga en cuenta que el nombre de la interfaz comienza con un carácter de subrayado. Esta es una Convención para indicar que la interfaz es una interfaz interna. Por lo tanto, los programas que permiten examinar objetos COM pueden optar por no mostrar la interfaz al usuario. Además, tenga en cuenta que la selección de **puntos de conexión** agrega la siguiente línea en el archivo Polygon. idl para indicar que `_IPolyCtlEvents` es la interfaz de origen predeterminada:

`[default, source] dispinterface _IPolyCtlEvents;`

El atributo de origen indica que el control es el origen de las notificaciones, por lo que llamará a esta interfaz en el contenedor.

Ahora, agregue los métodos `ClickIn` y `ClickOut` a la interfaz `_IPolyCtlEvents`.

### <a name="to-add-the-clickin-and-clickout-methods"></a>Para agregar los métodos Clickism y ClickOut

1. En **Explorador de soluciones**, abra Polygon. idl y agregue el código siguiente en `methods:` en la declaración de `dispInterface_IPolyCtlEvents` de la biblioteca PolygonLib:

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

Los métodos `ClickIn` y `ClickOut` toman como parámetros las coordenadas x e y del punto en el que se hace clic.

## <a name="generating-the-type-library"></a>Generar la biblioteca de tipos

Genere la biblioteca de tipos en este momento, porque el proyecto la usará para obtener la información que necesita para construir una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control.

### <a name="to-generate-the-type-library"></a>Para generar la biblioteca de tipos

1. Vuelva a compilar el proyecto.

     O bien

1. Haga clic con el botón secundario en el archivo Polygon. idl en **Explorador de soluciones** y haga clic en **compilar** en el menú contextual.

Esto creará el archivo Polygon. tlb, que es la biblioteca de tipos. El archivo Polygon. tlb no es visible desde **Explorador de soluciones**, porque es un archivo binario y no se puede ver ni modificar directamente.

## <a name="implementing-the-connection-point-interfaces"></a>Implementar las interfaces de punto de conexión

Implemente una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control. En COM, los eventos se implementan a través del mecanismo de puntos de conexión. Para recibir eventos de un objeto COM, un contenedor establece una conexión de consulta con el punto de conexión que el objeto COM implementa. Dado que un objeto COM puede tener varios puntos de conexión, el objeto COM también implementa una interfaz de contenedor de punto de conexión. A través de esta interfaz, el contenedor puede determinar qué puntos de conexión se admiten.

La interfaz que implementa un punto de conexión se denomina `IConnectionPoint`, y la interfaz que implementa un contenedor de puntos de conexión se denomina `IConnectionPointContainer`.

Para ayudar a implementar `IConnectionPoint`, utilizará el Asistente para implementar puntos de conexión. Este asistente genera la interfaz `IConnectionPoint` leyendo la biblioteca de tipos e implementando una función para cada evento que se puede desencadenar.

### <a name="to-implement-the-connection-points"></a>Para implementar los puntos de conexión

1. En **Explorador de soluciones**, abra _IPolyCtlEvents_CP. h y agregue el código siguiente bajo la instrucción `public:` en la clase `CProxy_IPolyCtlEvents`:

    ```cpp
    VOID Fire_ClickIn(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x1, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    VOID Fire_ClickOut(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x2, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    ```

Verá que este archivo tiene una clase denominada `CProxy_IPolyCtlEvents` que se deriva de `IConnectionPointImpl`. _IPolyCtlEvents_CP. h define ahora los dos métodos `Fire_ClickIn` y `Fire_ClickOut`, que toman los dos parámetros de coordenadas. Puede llamar a estos métodos cuando desee activar un evento desde el control.

Al crear la opción control con **puntos de conexión** seleccionada, se genera el archivo _IPolyCtlEvents_CP. h. También se ha agregado `CProxy_PolyEvents` y `IConnectionPointContainerImpl` a la lista de herencia múltiple del control y se ha expuesto `IConnectionPointContainer` automáticamente agregando las entradas adecuadas al mapa COM.

Ha terminado de implementar el código para admitir eventos. Ahora, agregue código para desencadenar los eventos en el momento adecuado. Recuerde que va a activar un `ClickIn` o `ClickOut` evento cuando el usuario hace clic con el botón primario del mouse en el control. Para averiguar cuándo el usuario hace clic en el botón, agregue un controlador para el mensaje de `WM_LBUTTONDOWN`.

### <a name="to-add-a-handler-for-the-wm_lbuttondown-message"></a>Para agregar un controlador para el mensaje WM_LBUTTONDOWN

1. En **vista de clases**, haga clic con el botón secundario en la clase `CPolyCtl` y haga clic en **propiedades** en el menú contextual.

1. En la ventana **propiedades** , haga clic en el icono **mensajes** y, a continuación, haga clic en `WM_LBUTTONDOWN` de la lista de la izquierda.

1. En la lista desplegable que aparece, haga clic en **\<agregar > OnLButtonDown**. La declaración del controlador de `OnLButtonDown` se agregará a PolyCtl. h y la implementación del controlador se agregará a PolyCtl. cpp.

A continuación, modifique el controlador.

### <a name="to-modify-the-onlbuttondown-method"></a>Para modificar el método OnLButtonDown

1. Cambie el código que comprende el método `OnLButtonDown` en PolyCtl. cpp (eliminando cualquier código colocado por el asistente) para que tenga el aspecto siguiente:

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Este código hace uso de los puntos calculados en la función `OnDraw` para crear una región que detecta los clics del mouse del usuario con la llamada a `PtInRegion`.

El parámetro *uMsg* es el identificador del mensaje de Windows que se está controlando. Esto le permite tener una función que controla un intervalo de mensajes. Los parámetros *wParam* y *lParam* son los valores estándar para el mensaje que se está controlando. El parámetro *bHandled* le permite especificar si la función controló el mensaje o no. De forma predeterminada, el valor se establece en TRUE para indicar que la función controló el mensaje, pero puede establecerlo en FALSE. Esto hará que ATL siga buscando otra función de controlador de mensajes a la que enviar el mensaje.

## <a name="building-and-testing-the-control"></a>Compilar y probar el control

Ahora pruebe los eventos. Compile el control e inicie de nuevo el contenedor de pruebas de control ActiveX. Esta vez, vea la ventana registro de eventos. Para enrutar los eventos a la ventana de salida, haga clic en **registro** en el menú **Opciones** y seleccione **registrar en la ventana de salida**. Inserte el control e intente hacer clic en la ventana. Tenga en cuenta que `ClickIn` se activa si hace clic en el polígono relleno y `ClickOut` se activa al hacer clic fuera de él.

A continuación, agregará una página de propiedades.

[Volver al paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [en el paso 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Consulte también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
