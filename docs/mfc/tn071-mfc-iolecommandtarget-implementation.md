---
title: 'TN071: Implementación de IOleCommandTarget en MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 56745e7985c8af97b0b628d148586ccef346d95a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442074"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: Implementación de IOleCommandTarget en MFC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

La interfaz `IOleCommandTarget` permite que los objetos y sus contenedores envíen comandos entre sí. Por ejemplo, las barras de herramientas de un objeto pueden contener botones para comandos como `Print`, `Print Preview`, `Save`, `New`y `Zoom`. Si este tipo de objeto se incrustó en un contenedor que admite `IOleCommandTarget`, el objeto podría habilitar sus botones y reenviar los comandos al contenedor para su procesamiento cuando el usuario hace clic en ellos. Si un contenedor deseara que el objeto incrustado se imprimiera, podría hacer esta solicitud mediante el envío de un comando a través de la interfaz `IOleCommandTarget` del objeto incrustado.

`IOleCommandTarget` es una interfaz similar a la de automatización en que un cliente la usa para invocar métodos en un servidor. Sin embargo, el uso de `IOleCommandTarget` ahorra la sobrecarga de realizar llamadas a través de las interfaces de automatización porque los programadores no tienen que usar el método de `IDispatch`de `Invoke` que suele ser costoso.

En MFC, los servidores de documentos activos utilizan la interfaz de `IOleCommandTarget` para permitir que los contenedores de documentos activos envíen comandos al servidor. La clase de servidor de documentos activa, `CDocObjectServerItem`, utiliza mapas de interfaz de MFC (vea [TN038: implementación de IUnknown en MFC/OLE](../mfc/tn038-mfc-ole-iunknown-implementation.md)) para implementar la interfaz de `IOleCommandTarget`.

`IOleCommandTarget` también se implementa en la clase `COleFrameHook`. `COleFrameHook` es una clase MFC no documentada que implementa la funcionalidad de la ventana de marco de los contenedores de edición en contexto. `COleFrameHook` también utiliza mapas de interfaz de MFC para implementar la interfaz de `IOleCommandTarget`. la implementación de `COleFrameHook`de `IOleCommandTarget` reenvía comandos OLE a contenedores de documentos activos derivados de `COleDocObjectItem`. Esto permite que cualquier contenedor de documentos activos MFC reciba mensajes de servidores de documentos activos contenidos.

## <a name="mfc-ole-command-maps"></a>Mapas de comandos OLE de MFC

Los desarrolladores de MFC pueden aprovechar las ventajas de `IOleCommandTarget` mediante el uso de mapas de comandos OLE de MFC. Las asignaciones de comandos OLE son similares a las asignaciones de mensajes porque se pueden usar para asignar comandos OLE a funciones miembro de la clase que contiene el mapa de comandos. Para que esto funcione, coloque las macros en el mapa de comandos para especificar el grupo de comandos OLE del comando que desea controlar, el comando OLE y el identificador de comando del mensaje [WM_COMMAND](/windows/win32/menurc/wm-command) que se enviará cuando se reciba el comando OLE. MFC también proporciona varias macros predefinidas para los comandos OLE estándar. Para obtener una lista de los comandos OLE estándar que se diseñaron originalmente para usarlos con Microsoft Office aplicaciones, consulte la enumeración OLECMDID, que se define en docobj. h.

Cuando una aplicación MFC que contiene un mapa de comandos OLE recibe un comando OLE, MFC intenta buscar el identificador de comando y el grupo de comandos para el comando solicitado en el mapa de comandos OLE de la aplicación. Si se encuentra una coincidencia, se envía un mensaje WM_COMMAND a la aplicación que contiene el mapa de comandos con el identificador del comando solicitado. (Vea la descripción de `ON_OLECMD` a continuación). De esta manera, los comandos OLE enviados a una aplicación se convierten en WM_COMMAND mensajes mediante MFC. A continuación, los mensajes de WM_COMMAND se enrutan a través de los mapas de mensajes de la aplicación mediante la arquitectura de [enrutamiento de comandos](../mfc/command-routing.md) estándar de MFC.

A diferencia de los mapas de mensajes, las asignaciones de comandos OLE de MFC no se admiten en ClassWizard. Los desarrolladores de MFC deben agregar manualmente las entradas de asignación de comandos OLE y de asignación de comandos OLE. Los mapas de comandos OLE se pueden agregar a los servidores de documentos activos MFC en cualquier clase que se encuentra en el WM_COMMAND cadena de enrutamiento de mensajes en el momento en que el documento activo está activo en contexto en un contenedor. Estas clases incluyen las clases de la aplicación derivadas de [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md)y [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). En los contenedores de documentos activos, los mapas de comandos OLE solo se pueden agregar a la clase derivada de [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md). Además, en los contenedores de documentos activos, los mensajes de WM_COMMAND solo se enviarán al mapa de mensajes en la clase derivada de `COleDocObjectItem`.

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
IDENTIFICADOR del mensaje de WM_COMMAND que se va a enviar a la aplicación que contiene el mapa de comandos cuando se invoca este comando OLE.

Use la macro ON_OLECMD en el mapa de comandos para agregar entradas para los comandos OLE que desea controlar. Cuando se reciben los comandos OLE, se convertirán en el mensaje de WM_COMMAND especificado y se enrutarán a través del mapa de mensajes de la aplicación mediante la arquitectura estándar de enrutamiento de comandos de MFC.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo agregar la funcionalidad de control de comandos OLE a un servidor de documentos activo de MFC para controlar el comando OLE de [OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) . En este ejemplo se da por supuesto que ha usado AppWizard para generar una aplicación MFC que es un servidor de documentos activos.

1. En el archivo de encabezado de la clase derivada de `CView`, agregue la macro DECLARE_OLECMD_MAP a la declaración de clase.

    > [!NOTE]
    > Utilice la clase derivada de `CView`porque es una de las clases del servidor de documentos activo que se encuentra en la cadena de enrutamiento de mensajes WM_COMMAND.

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

2. En el archivo de implementación de la clase derivada de `CView`, agregue las macros BEGIN_OLECMD_MAP y END_OLECMD_MAP:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Para controlar el comando estándar de impresión OLE, agregue una macro [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) al mapa de comandos especificando el identificador de comando OLE para el comando de impresión estándar y **ID_FILE_PRINT** para el ID. de WM_COMMAND. **ID_FILE_PRINT** es el identificador de comando de impresión estándar que usan las aplicaciones MFC generadas por AppWizard:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Tenga en cuenta que se puede usar una de las macros de comandos OLE estándar, que se define en afxdocob. h, en lugar de la macro ON_OLECMD porque **OLECMDID_PRINT** es un identificador de comando OLE estándar. La macro ON_OLECMD_PRINT llevará a cabo la misma tarea que la macro ON_OLECMD mostrada anteriormente.

Cuando una aplicación contenedora envía a este servidor un comando **OLECMDID_PRINT** a través de la interfaz de `IOleCommandTarget` del servidor, el controlador de comandos de impresión de MFC se invocará en el servidor, lo que hará que el servidor imprima la aplicación. El código del contenedor del documento activo para invocar el comando de impresión agregado en los pasos anteriores tendría un aspecto similar al siguiente:

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

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
