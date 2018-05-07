---
title: 'TN071: Implementación de IOleCommandTarget en MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21745762fb6f6eb1eb324013db12207c4b3b81d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: Implementación de IOleCommandTarget en MFC
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 El `IOleCommandTarget` interfaz permite que los objetos y sus contenedores para enviar comandos entre sí. Por ejemplo, las barras de herramientas de un objeto pueden contener botones para ejecutar comandos como **impresión**, **vista previa de impresión**, **guardar**, `New`, y **Zoom**. Si este tipo de objeto se incrusta en un contenedor que admite `IOleCommandTarget`, el objeto podría habilitar sus botones y reenviar los comandos para el contenedor para el procesamiento cuando el usuario hace clic en ellos. Si el objeto incrustado que se imprima de disfrutar de un contenedor, puede realizar esta solicitud mediante el envío de un comando a través de la `IOleCommandTarget` interfaz del objeto incrustado.  
  
 `IOleCommandTarget` es una interfaz de automatización en que se utiliza un cliente para invocar métodos en un servidor. No obstante, el uso `IOleCommandTarget` evita la sobrecarga de llamadas a través de interfaces de automatización porque los programadores no tienen que usar suele ser caro `Invoke` método `IDispatch`.  
  
 En MFC, la `IOleCommandTarget` interfaz se usa por servidores de documentos activos para permitir que los contenedores de documentos activos enviar comandos al servidor. La clase de servidor de documento activo, `CDocObjectServerItem`, utiliza los mapas de interfaz MFC (vea [TN038: implementación de IUnknown en MFC/OLE](../mfc/tn038-mfc-ole-iunknown-implementation.md)) para implementar el `IOleCommandTarget` interfaz.  
  
 `IOleCommandTarget` También se implementa en el **COleFrameHook** clase. **COleFrameHook** es una clase MFC sin documentar que implementa la funcionalidad de la ventana de marco en lugar de edición contenedores. **COleFrameHook** también usa los mapas de interfaz MFC para implementar la `IOleCommandTarget` interfaz. **COleFrameHook**de implementación de `IOleCommandTarget` envía comandos OLE a `COleDocObjectItem`-derivado contenedores de documentos activos. Esto permite que cualquier contenedor de documentos activo de MFC recibir mensajes desde servidores de documentos activos independientes.  
  
## <a name="mfc-ole-command-maps"></a>Mapas de comando OLE de MFC  
 Los desarrolladores de MFC pueden aprovechar las ventajas de `IOleCommandTarget` mediante MFC OLE comando mapas. Mapas de comandos OLE son como mapas de mensajes, ya que se pueden usar para comandos OLE se asignan a las funciones miembro de la clase que contiene el mapa de comando. Para solucionar este problema, coloque las macros en la asignación de comandos para especificar el grupo de comando OLE del comando que desea administrar, el comando OLE y el identificador de comando de la [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje que se enviará cuando se recibe el comando OLE. MFC también proporciona una serie de macros predefinidas para los comandos estándar de OLE. Para obtener una lista de lo estándar OLE comandos que se diseñaron originalmente para usar con aplicaciones de Microsoft Office, vea la enumeración OLECMDID, que se define en docobj.h.  
  
 Cuando se recibe un comando OLE por una aplicación MFC que contiene un mapa de comando OLE, MFC intenta encontrar el identificador de comando y el grupo de comandos para el comando solicitado en el mapa de comando OLE de la aplicación. Si se encuentra una coincidencia, un **WM_COMMAND** mensaje se envía a la aplicación que contiene la asignación de comandos con el identificador del comando solicitado. (Vea la descripción de `ON_OLECMD` a continuación.) De esta manera, los comandos OLE que se envían a una aplicación se convierten en **WM_COMMAND** mensajes por MFC. El **WM_COMMAND** , a continuación, los mensajes se enrutan a través de mapas de mensajes de la aplicación mediante el estándar MFC [enrutamiento de comandos](../mfc/command-routing.md) arquitectura.  
  
 A diferencia de los mapas de mensajes, ClassWizard no admite mapas de comandos OLE de MFC. Los desarrolladores de MFC deben agregar manualmente entradas de mapa de comando OLE y compatibilidad con asignación de comando OLE. OLE mapas de comandos se pueden agregar a los servidores de documentos activos de MFC en cualquier clase que se encuentra en la **WM_COMMAND** cadena de enrutamiento de mensajes en el tiempo en el documento activo está activo en contexto en un contenedor. Estas clases incluyen las clases de la aplicación que se derivan de [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md), y [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). En contenedores de documentos activos, los mapas de comandos OLE solo pueden agregarse a la [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-clase derivada. Además, en contenedores de documentos activos, el **WM_COMMAND** sólo se enviarán mensajes para el mapa de mensajes en el `COleDocObjectItem`-clase derivada.  
  
## <a name="ole-command-map-macros"></a>Macros de mapa de comando OLE  
 Use las macros siguientes para agregar la funcionalidad de mapas de comando a la clase:  
  
```  
 
DECLARE_OLECMD_MAP ()  
 
```  
  
 Esta macro va en la declaración de clase (normalmente en el archivo de encabezado) de la clase que contiene el mapa de comando.  
  
```  
 
BEGIN_OLECMD_MAP(
theClass  ,   baseClass)  
 
```  
  
 `theClass`  
 Nombre de la clase que contiene la asignación de comandos.  
  
 `baseClass`  
 Nombre de la clase base de la clase que contiene el mapa de comando.  
  
 Esta macro marca el principio de la asignación de comandos. Use esta macro en el archivo de implementación para la clase que contiene la asignación de comandos.  
  
```  
 
END_OLECMD_MAP()  
 
```  
  
 Esta macro marca el final de la asignación de comandos. Use esta macro en el archivo de implementación para la clase que contiene la asignación de comandos. Esta macro siempre debe seguir la **BEGIN_OLECMD_MAP** macro.  
  
```  
 
ON_OLECMD(
pguid  ,   
olecmdid  ,
    id)  
 
```  
  
 `pguid`  
 Puntero al GUID del grupo de comandos del comando OLE. Este parámetro es **NULL** para el grupo de comandos OLE estándar.  
  
 *olecmdid*  
 Identificador de comando OLE del comando que se debe invocar.  
  
 `id`  
 Id. de la **WM_COMMAND** mensaje que se enviará a la aplicación que contiene la asignación de comandos cuando se invoca este comando OLE.  
  
 Use la `ON_OLECMD` comandos de macro en el mapa de comando para agregar entradas para OLE que desea controlar. Cuando se reciben los comandos OLE, se convertirá a especificado **WM_COMMAND** el mensaje y enruta a través del mapa de mensajes de la aplicación con la arquitectura de enrutamiento de comandos MFC estándar.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar funcionalidad de control de comando OLE a un servidor de documentos activos de MFC para controlar la [OLECMDID_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) comando OLE. En este ejemplo se da por supuesto que usa el Asistente para aplicaciones para generar una aplicación MFC que sea un servidor de documento activo.  
  
1.  En su `CView`-derivados de encabezado de la clase, agregue el `DECLARE_OLECMD_MAP` macro en la declaración de clase.  
  
    > [!NOTE]
    >  Use la `CView`-clase derivada porque es una de las clases en el servidor de documentos activos que se encuentra en la **WM_COMMAND** cadena de enrutamiento de mensajes.  
  
 ```  
    class CMyServerView : public CView  
 {  
    protected: // create from serialization only  
    CMyServerView();
DECLARE_DYNCREATE(CMyServerView)  
    DECLARE_OLECMD_MAP() 
 . . .  
 };  
 ```  
  
2.  En el archivo de implementación para la `CView`-clase derivada, agrega el `BEGIN_OLECMD_MAP` y `END_OLECMD_MAP` macros:  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
 
    END_OLECMD_MAP() 
 ```  
  
3.  Para controlar el comando de impresión estándar de OLE, agregue una [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) macro a la asignación de comandos especifica el identificador de comando OLE para el comando de impresión estándar y **ID_FILE_PRINT** para el **WM_COMMAND**  Identificador. **ID_FILE_PRINT** es el estándar usando el Id. de comando de impresión generado por el Asistente para aplicaciones MFC (aplicaciones):  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView,
    CView)  
    ON_OLECMD(NULL,
    OLECMDID_PRINT,
    ID_FILE_PRINT) 
    END_OLECMD_MAP() 
 ```  
  
 Tenga en cuenta que una de las macros de comando OLE estándares, definidas en afxdocob.h, podría usarse en lugar de la `ON_OLECMD` macro porque **OLECMDID_PRINT** es un identificador estándar del comando OLE. El `ON_OLECMD_PRINT` macro llevará a cabo la misma tarea que el `ON_OLECMD` macro mostrado anteriormente.  
  
 Cuando una aplicación de contenedor envía este servidor un **OLECMDID_PRINT** comando a través del servidor `IOleCommandTarget` interfaz, el controlador de comandos de impresión de MFC se invocará en el servidor, lo que el servidor de impresión de la aplicación. Código del contenedor de documentos activos para invocar el comando de impresión agregado en los pasos anteriores sería algo parecido a esto:  
  
```  
void CContainerCntrItem::DoOleCmd()  
{  
    IOleCommandTarget *pCmd = NULL;  
    HRESULT hr = E_FAIL;  
    OLECMD ocm={OLECMDID_PRINT, 0};  
 
    hr = m_lpObject->QueryInterface(IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if(FAILED(hr)) 
    return; 
 
    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if(SUCCEEDED(hr)&& (ocm.cmdf& OLECMDF_ENABLED))  
 { *//Command is available and enabled so call it  
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
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

