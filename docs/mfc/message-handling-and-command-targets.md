---
title: "Control de mensajes y destinos de comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "enrutamiento de comandos, destinos de comando"
  - "destinos de comando"
  - "IOleCommandTarget (interfaz)"
  - "control de mensajes, documentos activos"
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Control de mensajes y destinos de comando
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La interfaz de envío `IOleCommandTarget` de comando define un mecanismo sencillo y extensible ver y ejecutar comandos.  Este mecanismo es más sencillo que `IDispatch` de automatización porque se basa completamente en un conjunto estándar de comandos; los comandos tienen raramente argumentos, y no hay información de tipo implicada \(seguridad de tipos se disminuye para los argumentos del comando también\).  
  
 En el diseño de interfaz de envío de comando, cada comando pertenece a un “grupo de comando” que sí mismo se identifica con **GUID**.  Por consiguiente, cualquier persona puede definir un grupo y definir todos los comandos dentro de ese grupo sin necesidad de coordinar con Microsoft o cualquier otro proveedor. \(Este es esencialmente el mismo significa de definición como **dispinterface** más **dispIDs** en la automatización.  Hay superposición aquí, aunque este mecanismo de enrutamiento de comandos es solo para el enrutamiento de comandos y no para el script y programación a gran escala como identificadores de automatización\).  
  
 `IOleCommandTarget` controla los escenarios siguientes:  
  
-   Cuando un objeto se haber producido en contexto, solo las barras de herramientas del objeto se muestran habitualmente y barras de herramientas de objeto pueden tener botones para algunos de los comandos del contenedor como **Impresión**, **Impresión Vista previa**, **Guardar**, `New`, **Zoom**, y otros. \(Las normas de activación en contexto recomienda los objetos quitan como botones de las barras de herramientas, o al menos las deshabilitados.  Este diseño permite habilitar pero son enrutados a esos comandos el controlador apropiado.\) Actualmente, no hay ningún mecanismo para que el objeto enviar estos comandos al contenedor.  
  
-   Cuando un documento activo se incrusta en un contenedor de documento activo \(como Office binder\), el contenedor puede necesitar enviar los comandos tal **Impresión**, **Página Programa de instalación**, **Propiedades**, et al documento activo contenido.  
  
 Este enrutamiento de comandos simple se puede controlar con estándares existentes y `IDispatch`de automatización.  Sin embargo, la sobrecarga implicada con `IDispatch` es más necesario aquí, por lo que `IOleCommandTarget` proporciona un más simple significa lograr los mismos fines:  
  
 `interface IOleCommandTarget : IUnknown`  
  
 `{`  
  
 `HRESULT QueryStatus(`  
  
 `[in] GUID *pguidCmdGroup,`  
  
 `[in] ULONG cCmds,`  
  
 `[in,out][size_is(cCmds)] OLECMD *prgCmds,`  
  
 `[in,out] OLECMDTEXT *pCmdText);`  
  
 `HRESULT Exec(`  
  
 `[in] GUID *pguidCmdGroup,`  
  
 `[in] DWORD nCmdID,`  
  
 `[in] DWORD nCmdExecOpt,`  
  
 `[in] VARIANTARG *pvaIn,`  
  
 `[in,out] VARIANTARG *pvaOut);`  
  
 `}`  
  
 El método de `QueryStatus` aquí prueba si se admite un conjunto de comandos, el conjunto de detalle que se identifica con **GUID**.  Esta llamada rellena una matriz de valores de **OLECMD** \(estructuras\) con la lista de comandos compatible así como devuelve el texto que describe el nombre de un comando o de la información de estado.  Cuando el llamador para invocar un comando, puede pasar el comando \(y **GUID**determinado\) a **Ejecución** junto con las opciones y argumentos, obtener la devuelve un valor devuelto.  
  
## Vea también  
 [Contenedores de documentos activos](../mfc/active-document-containers.md)