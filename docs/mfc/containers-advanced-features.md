---
title: "Contenedores: Caracter&#237;sticas avanzadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones de contenedor y servidor [C++]"
  - "contenedores [C++], características avanzadas"
  - "contenedores [C++], aplicaciones de contenedor"
  - "contenedores [C++], vínculos a los objetos incrustados de OLE"
  - "objetos incrustados [C++]"
  - "vínculos [C++], a objetos incrustados de OLE"
  - "contenedores OLE, características avanzadas"
  - "controles OLE, contenedores"
  - "aplicaciones de contenedor y servidor"
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Contenedores: Caracter&#237;sticas avanzadas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe los pasos necesarios para especificar características avanzadas opcionales en aplicaciones contenedoras existentes.  Estas características son:  
  
-   [Una aplicación que es un contenedor y servidor](#_core_creating_a_container.2f.server_application)  
  
-   [Un vínculo OLE a un objeto incrustado](#_core_links_to_embedded_objects)  
  
##  <a name="_core_creating_a_container.2f.server_application"></a> Crear un contenedor o una aplicación de servidor  
 Un contenedor o una aplicación de servidor es una aplicación que actúa como un contenedor y servidor.  Microsoft Word para Windows es un ejemplo de esto.  Puede insertar la palabra de los documentos de Windows en otras aplicaciones, y también puede insertar elementos en word para los documentos de Windows.  El proceso para modificar la aplicación contenedora para ser un contenedor y servidor completo \(no puede crear una aplicación de contenedor\/miniserver de combinación\) es similar al proceso para crear un servidor completo.  
  
 El artículo [Servidores: Implementar en un Servidor](../mfc/servers-implementing-a-server.md) muestra varias tareas necesarias para implementar una aplicación de servidor.  Si convierte una aplicación contenedora para un contenedor\/aplicación de servidor, hay que realizar algunas de estas mismas tareas, agregando código al contenedor.  A continuación se enumeran las cosas importantes para ver:  
  
-   El código de contenedor creado por el asistente para aplicaciones inicializa ya el subsistema OLE.  No necesitará cambiar o agregar nada para ese compatibilidad.  
  
-   Clase base de una clase de documento es siempre que `COleDocument`, cambie la clase base a `COleServerDoc`.  
  
-   Reemplace `COleClientItem::CanActivate` para evitar editar elementos en el lugar mientras estén utilizando el propio servidor para la edición en contexto.  
  
     Por ejemplo, el ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md) MFC ha insertado un elemento creado por el contenedor o la aplicación de servidor.  Abra la aplicación OCLIENT y la edición en contexto que el elemento creado por el contenedor o la aplicación de servidor.  Mientras edita el elemento application, decide que desea insertar un elemento creado en el ejemplo OLE [HIERSVR](../top/visual-cpp-samples.md)MFC.  Para ello, no puede utilizar la activación en contexto.  Debe abrir totalmente HIERSVR para activar este elemento.  Dado que la biblioteca Microsoft Foundation Class no admite esta característica OLE, reemplazar `COleClientItem::CanActivate` permite comprobar si hay esta situación y que evita un error en tiempo de ejecución posible en la aplicación.  
  
 Si está creando una nueva aplicación y desea trabajar como un contenedor o una aplicación de servidor, elija que la opción en el cuadro de diálogo Y opciones del asistente para aplicaciones y esta compatibilidad se creará automáticamente.  Para obtener más información, vea el artículo [Información general: Crear un contenedor de controles ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md).  Para obtener información sobre los ejemplos de MFC, vea los ejemplos de MFC.  
  
 Observe que no puede incrustar una aplicación MDI en sí mismo.  Una aplicación que es un contenedor\/servidor no se pueden insertar en sí mismo a menos que sea una aplicación SDI.  
  
##  <a name="_core_links_to_embedded_objects"></a> Vínculos a los objetos incrustados  
 Los vínculos a la característica de los objetos incrustados permiten a un usuario para crear un documento con un vínculo OLE a un objeto incrustado en la aplicación contenedora.  Por ejemplo, cree un documento en un procesador de textos que contiene una hoja de cálculo incrustada.  Si la aplicación admite vínculos a los objetos incrustados, puede pegar un vínculo a la hoja de cálculo contenida en el documento de procesador de textos.  Esta característica permite la aplicación para utilizar la información contenida en la hoja de cálculo sin saber dónde el procesador de textos la obtuvo originalmente.  
  
#### Para vincular a los objetos incrustados en la aplicación  
  
1.  Derive la clase de `COleLinkingDoc` en lugar de `COleDocument`.  
  
2.  Cree un identificador de la clase OLE \(**CLSID**\) para la aplicación utilizando el identificador Generador de la clase incluida con las herramientas de desarrollo de OLE.  
  
3.  Registre la aplicación con OLE.  
  
4.  Cree un objeto de `COleTemplateServer` como miembro de clase de aplicación.  
  
5.  En la función miembro de `InitInstance` de clase de aplicación, haga lo siguiente:  
  
    -   Conectar el objeto de `COleTemplateServer` a las plantillas de documento llamando a la función miembro de `ConnectTemplate` del objeto.  
  
    -   Llame a la función miembro de **COleTemplateServer::RegisterAll** para registrar todos los objetos de clase con el sistema OLE.  
  
    -   Llamar a `COleTemplateServer::UpdateRegistry`.  El único parámetro a `UpdateRegistry` debe ser `OAT_CONTAINER` si la aplicación no se inicia con el modificador “\/Embedded”.  Esto registra la aplicación como contenedor que puede admitir vínculos a objetos incrustados.  
  
         Si la aplicación se inicia con el modificador “\/Embedded”, no debe mostrar la ventana principal, similar a una aplicación de servidor.  
  
 El ejemplo [OCLIENT](../top/visual-cpp-samples.md) MFC OLE implementa esta característica.  Para obtener un ejemplo de cómo se hace esto, vea la función de `InitInstance` en el archivo de OCLIENT.CPP de esta aplicación de ejemplo.  
  
## Vea también  
 [Contenedores](../mfc/containers.md)   
 [Servidores](../mfc/servers.md)