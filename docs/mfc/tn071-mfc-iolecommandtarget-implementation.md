---
title: 'TN071: Implementación de IOleCommandTarget en MFC'
ms.date: 06/28/2018
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 7077211396c68750d47b91c7b2bb113370990f62
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511099"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: Implementación de IOleCommandTarget en MFC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

La `IOleCommandTarget` interfaz permite que los objetos y sus contenedores envíen comandos entre sí. Por ejemplo, las barras de herramientas de un objeto pueden contener botones para comandos `Print`como `Print Preview` `Save`,, `New`, y `Zoom`. Si este tipo de objeto se incrustó en un contenedor compatible `IOleCommandTarget`con, el objeto podría habilitar sus botones y reenviar los comandos al contenedor para su procesamiento cuando el usuario hace clic en ellos. Si un contenedor deseara que el objeto incrustado se imprimiera, podría hacer esta solicitud mediante el envío de `IOleCommandTarget` un comando a través de la interfaz del objeto incrustado.

`IOleCommandTarget`es una interfaz similar a la de automatización en que un cliente la usa para invocar métodos en un servidor. Sin embargo, `IOleCommandTarget` el uso de evita la sobrecarga de realizar llamadas a través de las interfaces de automatización `Invoke` , ya que los programadores no tienen que usar el método de `IDispatch`.

En MFC, los `IOleCommandTarget` servidores de documentos activos utilizan la interfaz para permitir que los contenedores de documentos activos envíen comandos al servidor. La clase de servidor de documentos `CDocObjectServerItem`activa,, usa mapas de interfaz [de MFC (vea TN038: Implementación](../mfc/tn038-mfc-ole-iunknown-implementation.md)IUnknown de MFC/OLE) para implementar `IOleCommandTarget` la interfaz.

`IOleCommandTarget`también se implementa en la `COleFrameHook` clase. `COleFrameHook`es una clase MFC no documentada que implementa la funcionalidad de la ventana de marco de los contenedores de edición en contexto. `COleFrameHook`también utiliza mapas de interfaz de MFC para `IOleCommandTarget` implementar la interfaz. `COleFrameHook`la implementación de `IOleCommandTarget` de reenvía comandos `COleDocObjectItem`OLE a contenedores de documentos activos derivados. Esto permite que cualquier contenedor de documentos activos MFC reciba mensajes de servidores de documentos activos contenidos.

## <a name="mfc-ole-command-maps"></a>Mapas de comandos OLE de MFC

Los desarrolladores de MFC pueden aprovechar `IOleCommandTarget` las ventajas de mediante el uso de mapas de comandos OLE de MFC. Las asignaciones de comandos OLE son similares a las asignaciones de mensajes porque se pueden usar para asignar comandos OLE a funciones miembro de la clase que contiene el mapa de comandos. Para que esto funcione, coloque las macros en el mapa de comandos para especificar el grupo de comandos OLE del comando que desea controlar, el comando OLE y el identificador de comando del mensaje [WM_COMMAND](/windows/win32/menurc/wm-command) que se enviará cuando se reciba el comando OLE. MFC también proporciona varias macros predefinidas para los comandos OLE estándar. Para obtener una lista de los comandos OLE estándar que se diseñaron originalmente para usarlos con Microsoft Office aplicaciones, consulte la enumeración OLECMDID, que se define en docobj. h.

Cuando una aplicación MFC que contiene un mapa de comandos OLE recibe un comando OLE, MFC intenta buscar el identificador de comando y el grupo de comandos para el comando solicitado en el mapa de comandos OLE de la aplicación. Si se encuentra una coincidencia, se envía un mensaje WM_COMMAND a la aplicación que contiene el mapa de comandos con el identificador del comando solicitado. (Consulte la descripción `ON_OLECMD` siguiente). De esta manera, MFC convierte los comandos OLE enviados en una aplicación en mensajes WM_COMMAND. Los mensajes WM_COMMAND se enrutan a través de los mapas de mensajes de la aplicación mediante la arquitectura de [enrutamiento de comandos](../mfc/command-routing.md) estándar de MFC.

A diferencia de los mapas de mensajes, las asignaciones de comandos OLE de MFC no se admiten en ClassWizard. Los desarrolladores de MFC deben agregar manualmente las entradas de asignación de comandos OLE y de asignación de comandos OLE. Los mapas de comandos OLE se pueden agregar a los servidores de documentos activos de MFC en cualquier clase que se encuentra en la cadena de enrutamiento de mensajes WM_COMMAND en el momento en que el documento activo está activo en contexto en un contenedor. Estas clases incluyen las clases de la aplicación derivadas de [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md)y [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). En los contenedores de documentos activos, los mapas de comandos OLE solo se pueden agregar a la clase derivada de [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md). Además, en contenedores de documentos activos, los mensajes WM_COMMAND solo se enviarán al mapa de mensajes en la `COleDocObjectItem`clase derivada de.

## <a name="ole-command-map-macros"></a>Macros de mapa de comandos OLE

Use las macros siguientes para agregar la funcionalidad de asignación de comandos a la clase:

```cpp
DECLARE_OLECMD_MAP ()
```

Esta macro va en la declaración de clase (normalmente en el archivo de encabezado) de la clase que contiene el mapa de comandos.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*Clase*<br/>
Nombre de la clase que contiene el mapa de comandos.

*baseClass*<br/>
Nombre de la clase base de la clase que contiene el mapa de comandos.

Esta macro marca el principio del mapa de comandos. Use esta macro en el archivo de implementación de la clase que contiene el mapa de comandos.

```
END_OLECMD_MAP()
```

Esta macro marca el final del mapa de comandos. Use esta macro en el archivo de implementación de la clase que contiene el mapa de comandos. Esta macro siempre debe seguir la macro BEGIN_OLECMD_MAP.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Puntero al GUID del grupo de comandos del comando OLE. Este parámetro es **null** para el grupo de comandos OLE estándar.

*olecmdid*<br/>
IDENTIFICADOR del comando OLE del comando que se va a invocar.

*id*<br/>
IDENTIFICADOR del mensaje WM_COMMAND que se va a enviar a la aplicación que contiene la asignación de comandos cuando se invoca este comando OLE.

Use la macro ON_OLECMD en el mapa de comandos para agregar entradas para los comandos OLE que desea controlar. Cuando se reciben los comandos OLE, se convertirán al mensaje WM_COMMAND especificado y se enrutarán a través del mapa de mensajes de la aplicación mediante la arquitectura estándar de enrutamiento de comandos de MFC.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo agregar la funcionalidad de control de comandos OLE a un servidor de documentos de MFC activo para administrar el comando [OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) OLE. En este ejemplo se da por supuesto que ha usado AppWizard para generar una aplicación MFC que es un servidor de documentos activos.

1. En el `CView`archivo de encabezado de la clase derivada de, agregue la macro DECLARE_OLECMD_MAP a la declaración de clase.

    > [!NOTE]
    > Utilice la `CView`clase derivada de porque es una de las clases del servidor de documentos activo que se encuentra en la cadena de enrutamiento de mensajes WM_COMMAND.

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. En el archivo de implementación de `CView`la clase derivada de, agregue las macros BEGIN_OLECMD_MAP y END_OLECMD_MAP:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Para controlar el comando estándar de impresión OLE, agregue una macro [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) al mapa de comandos especificando el identificador del comando OLE para el comando Print estándar y **ID_FILE_PRINT** para el identificador WM_COMMAND. **ID_FILE_PRINT** es el identificador de comando de impresión estándar que usan las aplicaciones MFC generadas por AppWizard:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Tenga en cuenta que se puede usar una de las macros de comandos OLE estándar, que se define en afxdocob. h, en lugar de la macro ON_OLECMD porque **OLECMDID_PRINT** es un identificador de comando OLE estándar. La macro ON_OLECMD_PRINT llevará a cabo la misma tarea que la macro ON_OLECMD mostrada anteriormente.

Cuando una aplicación contenedora envía a este servidor un comando **OLECMDID_PRINT** a través `IOleCommandTarget` de la interfaz del servidor, el controlador de comandos de impresión de MFC se invocará en el servidor, lo que hará que el servidor imprima la aplicación. El código del contenedor del documento activo para invocar el comando de impresión agregado en los pasos anteriores tendría un aspecto similar al siguiente:

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
