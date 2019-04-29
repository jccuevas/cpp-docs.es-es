---
title: Agregar un evento (Tutorial de ATL, Parte 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: 57fc2adaadcca52cfc25736b5f9010fcb65a2ff0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252568"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Agregar un evento (Tutorial de ATL, Parte 5)

En este paso, agregará un `ClickIn` y un `ClickOut` eventos al control ATL. Desencadenará el `ClickIn` evento si el usuario hace clic dentro del polígono y fire `ClickOut` si el usuario hace clic fuera. Las tareas para agregar un evento son los siguientes:

- Agregar el `ClickIn` y `ClickOut` métodos

- Generar la biblioteca de tipos

- Implementación de las Interfaces de punto de conexión

## <a name="adding-the-clickin-and-clickout-methods"></a>Agregar los métodos ClickIn y ClickOut

Cuando el control ATL que creó en el paso 2, seleccionó la **puntos de conexión** casilla de verificación. Esto crea el `_IPolyCtlEvents` interfaz en el archivo Polygon.idl. Tenga en cuenta que el nombre de interfaz comienza con un carácter de subrayado. Esta es una convención para indicar que la interfaz es una interfaz interna. Por lo tanto, pueden elegir los programas que le permiten explorar los objetos COM no se muestre la interfaz para el usuario. Tenga en cuenta también que la selección **puntos de conexión** agregó la siguiente línea en el archivo Polygon.idl para indicar que `_IPolyCtlEvents` es la interfaz de origen predeterminada:

`[default, source] dispinterface _IPolyCtlEvents;`

El atributo de origen indica que el control es el origen de las notificaciones, por lo que llamará a esta interfaz en el contenedor.

Ahora, agregue el `ClickIn` y `ClickOut` métodos para la `_IPolyCtlEvents` interfaz.

### <a name="to-add-the-clickin-and-clickout-methods"></a>Para agregar los métodos ClickIn y ClickOut

1. En **el Explorador de soluciones**, abra Polygon.idl y agregue el siguiente código bajo `methods:` en el `dispInterface_IPolyCtlEvents` declaración de la biblioteca PolygonLib:

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

El `ClickIn` y `ClickOut` métodos toman la x y coordenadas del punto donde ha hecho clic como parámetros.

## <a name="generating-the-type-library"></a>Generar la biblioteca de tipos

Generar la biblioteca de tipos en este momento, porque el proyecto usará para obtener la información que necesita construir una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control.

### <a name="to-generate-the-type-library"></a>Para generar la biblioteca de tipos

1. Recompile el proyecto.

     -o bien-

1. Haga clic en el archivo Polygon.idl en **el Explorador de soluciones** y haga clic en **compilar** en el menú contextual.

Esto creará el archivo Polygon.tlb, que es la biblioteca de tipos. No es visible desde el archivo Polygon.tlb **el Explorador de soluciones**, porque es un archivo binario y no puede ver ni modificar directamente.

## <a name="implementing-the-connection-point-interfaces"></a>Implementación de las Interfaces de punto de conexión

Implementar una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control. En COM, los eventos se implementan a través del mecanismo de puntos de conexión. Para recibir eventos de un objeto COM, un contenedor establece una conexión de consulta al punto de conexión que el objeto COM implementa. Dado un objeto COM puede tener varios puntos de conexión, el objeto COM también implementa una interfaz de contenedor de punto de conexión. Mediante esta interfaz, el contenedor puede determinar qué puntos de conexión se admiten.

La interfaz que implementa un punto de conexión se denomina `IConnectionPoint`, y la interfaz que implementa un contenedor de punto de conexión se denomina `IConnectionPointContainer`.

Para ayudar a implementar `IConnectionPoint`, utilizará el Asistente para implementar puntos de conexión. Este asistente genera el `IConnectionPoint` interfaz mediante la lectura de la biblioteca de tipos e implementando una función por cada evento que se puede activar.

### <a name="to-implement-the-connection-points"></a>Para implementar los puntos de conexión

1. En **el Explorador de soluciones**, abra _IPolyCtlEvents_CP.h y agregue el siguiente código bajo el `public:` instrucción en el `CProxy_IPolyCtlEvents` clase:

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

Verá que este archivo tiene una clase denominada `CProxy_IPolyCtlEvents` que se deriva de `IConnectionPointImpl`. _IPolyCtlEvents_CP.h define ahora los dos métodos `Fire_ClickIn` y `Fire_ClickOut`, que toman los dos parámetros de coordenadas. Estos métodos se llaman cuando desea desencadenar un evento desde el control.

Creando el control con **puntos de conexión** opción seleccionada, el archivo _IPolyCtlEvents_CP.h se generó para usted. Se agregó también `CProxy_PolyEvents` y `IConnectionPointContainerImpl` a la lista de herencia múltiple de su control y exponen `IConnectionPointContainer` automáticamente mediante la adición de entradas correspondientes al mapa COM.

Ya ha terminado de implementar el código para admitir los eventos. Ahora, agregue código para activar los eventos en el momento adecuado. Recuerde que va a activar una `ClickIn` o `ClickOut` cuando el usuario hace clic en el botón primario del mouse en el control de eventos. Para averiguar cuándo el usuario hace clic en el botón, agregue un controlador para el `WM_LBUTTONDOWN` mensaje.

### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Para agregar un controlador para el mensaje WM_LBUTTONDOWN

1. En **vista de clases**, haga clic en el `CPolyCtl` clase y haga clic en **propiedades** en el menú contextual.

1. En el **propiedades** ventana, haga clic en el **mensajes** icono y, a continuación, haga clic en `WM_LBUTTONDOWN` en la lista de la izquierda.

1. En la lista desplegable que aparece, haga clic en  **\<Agregar > OnLButtonDown**. El `OnLButtonDown` declaración del controlador se agregarán a PolyCtl.h y la implementación del controlador se agregarán a PolyCtl.cpp.

A continuación, modifique el controlador.

### <a name="to-modify-the-onlbuttondown-method"></a>Para modificar el método OnLButtonDown

1. Cambiar el código que contiene el `OnLButtonDown` método PolyCtl.cpp (eliminando el código insertado el asistente) para que se parece a esto:

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Esto permite código calcula el uso de los puntos en el `OnDraw` función para crear una región que detecta los clics del usuario con la llamada a `PtInRegion`.

El *uMsg* parámetro es el identificador del mensaje de Windows está controlando. Esto le permite tener una función que controla un intervalo de mensajes. El *wParam* y *lParam* parámetros son los valores estándar para el mensaje que se está controlando. El parámetro *bHandled* le permite especificar si la función controló el mensaje o no. De forma predeterminada, el valor se establece en TRUE para indicar que la función controló el mensaje, pero se puede establecer en FALSE. Esto hará que ATL continuar buscando otra función de controlador de mensajes enviar el mensaje.

## <a name="building-and-testing-the-control"></a>Compilar y probar el control

Pruebe ahora los eventos. Compilar el control y vuelva a iniciar el Control ActiveX Test Container. Esta vez, abra la ventana de registro de eventos. Para enrutar eventos a la ventana de salida, haga clic en **registro** desde el **opciones** menú y seleccione **registro de la ventana de salida**. Insertar el control e intente hacer clic en la ventana. Tenga en cuenta que `ClickIn` se activa si hace clic dentro del polígono de relleno y `ClickOut` se desencadena al hacer clic fuera de él.

A continuación, agregará una página de propiedades.

[Vuelva al paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [con el paso 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Vea también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
