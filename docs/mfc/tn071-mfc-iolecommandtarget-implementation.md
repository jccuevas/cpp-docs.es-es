---
title: "TN071: Implementaci&#243;n de IOleCommandTarget en MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IOleCommandTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOleCommandTarget (interfaz)"
  - "TN071"
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN071: Implementaci&#243;n de IOleCommandTarget en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 La interfaz de `IOleCommandTarget` habilita objetos y sus contenedores a los comandos de envío entre sí.  Por ejemplo, barras de herramientas de un objeto pueden contener botones para los comandos como **Impresión**, **Vista previa de impresión**, **Guardar**, `New`, y **Zoom**.  Si el objeto se insertará en un contenedor que admite `IOleCommandTarget`, el objeto podría habilitar los botones y reenviar los comandos al contenedor para procesar cuando el usuario los hace clic.  Si un contenedor deseado para el objeto incrustado para imprimirse, podría hacer esta solicitud se envía un comando a través de la interfaz de `IOleCommandTarget` de objetos incrustados.  
  
 `IOleCommandTarget` es Automatización\- como interfaz en utilizada por un cliente para invocar métodos en un servidor.  Sin embargo, mediante `IOleCommandTarget` guarda la sobrecarga de realizar llamadas a través de interfaces de Automatización porque los programadores no tienen que utilizar el método normalmente costoso de `Invoke` de `IDispatch`.  
  
 En MFC, la interfaz de `IOleCommandTarget` usan los servidores del documento activo para permitir que los contenedores del documento activo envían comandos al servidor.  La clase de servidor de documentos activos, `CDocObjectServerItem`, utiliza mapas de interfaz de MFC \(vea [TN038: Implementación de MFC\/OLE IUnknown](../mfc/tn038-mfc-ole-iunknown-implementation.md)\) para implementar la interfaz de `IOleCommandTarget` .  
  
 `IOleCommandTarget` también se implementa en la clase de **COleFrameHook** .  **COleFrameHook** es una clase MFC indocumentada que implementa la funcionalidad de la ventana cuadro de los contenedores de la edición en contexto.  **COleFrameHook** también utiliza mapas de interfaz de MFC para implementar la interfaz de `IOleCommandTarget` .  La implementación de**COleFrameHook** de `IOleCommandTarget` transmite a los comandos de OLE `COleDocObjectItem`\- contenedores derivados del documento activo.  Esto permite a cualquier contenedor de documentos activos de MFC recibe mensajes de los servidores contenido del documento activo.  
  
## Mapas de OLE de comando de MFC  
 Los desarrolladores de MFC pueden aprovecharse de `IOleCommandTarget` mediante mapas de OLE de comando de MFC.  Los mapas de OLE de comando son los mapas de mensajes porque pueden utilizarse para asignar comandos de OLE a las funciones miembro de clases que contiene el mapa del comando.  Para crear el trabajo, macros en lugar del mapa de comando para especificar el grupo de comandos OLE del comando que desea controlar, el comando OLE, y el identificador del mensaje de [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) que se envía cuando reciben el comando OLE.  MFC también ofrece varias macros predefinidas para los comandos de OLE estándar.  Para obtener una lista de los comandos de OLE estándar que se han diseñado originalmente para el uso con aplicaciones de Microsoft Office, vea la enumeración de OLECMDID, que se define en docobj.h.  
  
 Cuando una aplicación MFC recibe un comando OLE que contiene un mapa de comando OLE, MFC intenta buscar el identificador de comando y el grupo de comando para el comando solicitado en el mapa del comando OLE de la aplicación.  Si se encuentra una coincidencia, un mensaje de **WM\_COMMAND** se envía a la aplicación que contiene el mapa de comando con el identificador de comando solicitado. \(Vea la descripción de `ON_OLECMD` más adelante.\) De esta manera, MFC activan los comandos de OLE enviados a una aplicación en los mensajes de **WM\_COMMAND** .  Los mensajes de **WM\_COMMAND** se enrutan a través de los mapas de mensajes de la aplicación mediante la arquitectura estándar de MFC [enrutamiento de comandos](../mfc/command-routing.md) .  
  
 A diferencia de mapas de mensajes, mapas de OLE de comando de MFC no admite ClassWizard.  Los desarrolladores de MFC deben agregar entradas admiten y VIEJAS VIEJAS del mapa del comando a mano.  Los mapas de OLE de comando se pueden agregar servidores de documentos activos de MFC en cualquier clase que está en la cadena de enrutamiento de mensajes de **WM\_COMMAND** que el documento activo es en ese momento activo en contexto en un contenedor.  Estas clases incluyen las clases application derivadas de [CWinApp](../mfc/reference/cwinapp-class.md), de [CView](../mfc/reference/cview-class.md), de [CDocument](../mfc/reference/cdocument-class.md), y de [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md).  En contenedores del documento activo, mapas de OLE de comando sólo se pueden agregar a [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)\- clase derivada.  Asimismo, en contenedores de documentos activos, los mensajes de **WM\_COMMAND** se enviará al mapa de mensajes en `COleDocObjectItem`\- clase derivada.  
  
## Macros VIEJAS de mapa de comando  
 Utilice las siguientes macros para agregar funcionalidad de mapa de comando a la clase:  
  
```  
  
DECLARE_OLECMD_MAP ()  
  
```  
  
 Esta macro entra en la declaración de clase \(normalmente en el archivo de encabezado\) de la clase que contiene el mapa del comando.  
  
```  
  
BEGIN_OLECMD_MAP(  
theClass  
,   
baseClass  
)  
  
```  
  
 `theClass`  
 Nombre de la clase que contiene el mapa del comando.  
  
 `baseClass`  
 Nombre de la clase base de la clase que contiene el mapa del comando.  
  
 Esta macro marca el principio del mapa del comando.  Use esta macro en el archivo de implementación de la clase que contiene el mapa del comando.  
  
```  
  
END_OLECMD_MAP()  
  
```  
  
 Esta macro marca el final del mapa del comando.  Use esta macro en el archivo de implementación de la clase que contiene el mapa del comando.  Esta macro debe seguir la macro de **BEGIN\_OLECMD\_MAP** .  
  
```  
  
ON_OLECMD(  
pguid  
,   
olecmdid  
,   
id  
)  
  
```  
  
 `pguid`  
 Puntero al GUID del grupo de comando OLE de comando.  Este parámetro es **nulo** para el grupo de comandos estándar OLE.  
  
 *olecmdid*  
 Identificador de comando OLE de comando de invocarlos.  
  
 `id`  
 Identificador de mensaje de **WM\_COMMAND** se envía a la aplicación que contiene el comando asignado cuando se invoca a este comando OLE.  
  
 Utilice la macro de `ON_OLECMD` en el mapa del comando para agregar las entradas de los comandos de OLE que desea controlar.  Cuando reciben los comandos OLE, se convertirán al mensaje especificado de **WM\_COMMAND** y enrutados a través de mensajes de la aplicación asignado mediante la arquitectura estándar de comando\- enrutamiento de MFC.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo agregar OLE comando\- que administra capacidad un servidor de documentos activos de MFC de controlar el comando de [OLECMDID\_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) OLE.  Este ejemplo supone que utilizó AppWizard para generar una aplicación MFC que es un servidor de documentos activos.  
  
1.  En `CView`\- el archivo de encabezado derivado de la clase, agregue la macro de `DECLARE_OLECMD_MAP` a la declaración de clase.  
  
    > [!NOTE]
    >  Utilice `CView`\- clase derivada porque es una de las clases en el servidor de documentos activos que está en la cadena de enrutamiento de mensajes de **WM\_COMMAND** .  
  
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
  
2.  En el archivo de implementación para `CView`\- la clase derivada, agrega las macros de `BEGIN_OLECMD_MAP` y de `END_OLECMD_MAP` :  
  
    ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
  
    END_OLECMD_MAP()  
    ```  
  
3.  Para controlar el comando de impresión estándar OLE, agregue una macro de [ON\_OLECMD](../Topic/ON_OLECMD.md) el comando asignado especificando el identificador de comando OLE para el comando de impresión estándar y **ID\_FILE\_PRINT** para la identificación de **WM\_COMMAND ID\_FILE\_PRINT** es el identificador estándar de comando de impresión utilizado por las aplicaciones AppWizard\- generadas de MFC:  
  
    ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
       ON_OLECMD(NULL,OLECMDID_PRINT,ID_FILE_PRINT)  
    END_OLECMD_MAP()  
    ```  
  
 Observe que una de las macros de comando VIEJAS estándar, definido en afxdocob.h, podría utilizar en lugar de la macro de `ON_OLECMD` porque **OLECMDID\_PRINT** es un identificador OLE estándar de comando  La macro de `ON_OLECMD_PRINT` va a realizar la misma tarea que la macro de `ON_OLECMD` mostrada anteriormente.  
  
 Cuando una aplicación contenedora envía este servidor un comando de **OLECMDID\_PRINT** a través de la interfaz de `IOleCommandTarget` de servidor, MFC que imprime el controlador de comandos se invocará en el servidor, haciendo que el servidor imprima la aplicación.  El código de contenedor de documentos activos para invocar el comando de impresión agregado en los pasos anteriores será parecido a:  
  
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
   if(SUCCEEDED(hr) && (ocm.cmdf & OLECMDF_ENABLED))  
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
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)