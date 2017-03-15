---
title: "Activaci&#243;n (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activar objetos"
  - "activación [C++]"
  - "activación [C++], elementos OLE incrustados"
  - "documentos, OLE"
  - "objetos incrustados"
  - "activación en contexto"
  - "activación en contexto, elementos vinculados e incrustados"
  - "OLE [C++], activación"
  - "OLE [C++], editar"
  - "OLE [C++], activación en contexto"
  - "activación de direcciones OLE"
  - "elementos OLE, edición visual"
  - "aplicaciones de servidor OLE, activación"
  - "edición visual"
  - "edición visual, activación"
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Activaci&#243;n (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica el rol de la activación de edición visual de los elementos de OLE.  Después de que un usuario ha insertado un elemento OLE en un documento contenedor, puede que sea utilizado.  Para ello, el usuario hace doble clic en el elemento, que produce ese elemento.  La actividad más frecuente para la activación está editando.  Muchos elementos de OLE actuales, cuando se activan para editar, haga los menús y barras de herramientas de la ventana actual del cuadro al cambio para reflejar que pertenecer a la aplicación de servidor que creó el elemento.  Este comportamiento, conocido como activación en contexto, permite que el usuario modifique cualquier elemento incrustado en un documento compuesto sin dejar la ventana de documento contenedor.  
  
 También es posible editar elementos de OLE incrustados en una ventana independiente.  Esto sucede si el contenedor o la aplicación de servidor no admite la activación en contexto.  En este caso, cuando el usuario hace doble clic en un elemento incrustado, la aplicación de servidor se inicia en una ventana independiente y el elemento incrustado aparece como su propio documento.  El usuario edita el elemento en esta ventana.  Cuando se completa la edición, el usuario cierra la aplicación de servidor y vuelve a la aplicación contenedora.  
  
 Como alternativa, el usuario puede elegir “editar abierto” al comando de **\<object\> Open** en el menú de **edición** .  Esto abre el objeto en una ventana independiente.  
  
> [!NOTE]
>  Editar elementos incrustados en una ventana independiente era el comportamiento estándar en la versión 1 de OLE, y algunas aplicaciones OLE sólo pueden admitir este estilo de edición.  
  
 Activación in situ promueve un enfoque documento\- y centrado en a la creación del documento.  El usuario puede tratar un documento compuesto como una entidad única, trabajar en él sin cambiar entre las aplicaciones.  Sin embargo, la activación de contexto se utiliza para los elementos incrustados, no para los elementos vinculados: se deben editar en otra ventana.  Esto es porque un elemento vinculado se almacena realmente en otro lugar.  La edición de un elemento vinculado tiene lugar dentro del contexto real de los datos, es decir, donde se almacenan los datos.  Editar un elemento vinculado en una ventana independiente recuerda al usuario que los datos pertenezca a otro documento.  
  
 MFC no admite la activación en contexto anidados.  Si compila un contenedor o una aplicación de servidor, e insertar ese contenedor\/servidor en otro contenedor y haber producido en contexto, no puede en contexto generar objetos incrustados en el.  
  
 Lo que sucede con un elemento incrustado si hace doble clic del usuario que dependen de verbos definidos para el elemento.  Para obtener información, vea [Activación: Verbos](../mfc/activation-verbs.md).  
  
## Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [Contenedores](../mfc/containers.md)   
 [Servidores](../mfc/servers.md)