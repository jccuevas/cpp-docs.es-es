---
title: "Portapapeles: Usar el mecanismo del Portapapeles de OLE | Microsoft Docs"
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
  - "aplicaciones [OLE], Portapapeles"
  - "Portapapeles [C++], formatos OLE"
  - "formatos [C++], Portapapeles para (OLE)"
  - "Portapapeles OLE"
  - "Portapapeles OLE, formatos"
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Portapapeles: Usar el mecanismo del Portapapeles de OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE utiliza formatos estándar y algunos formatos OLE\- específicos para transferir datos a través del portapapeles.  
  
 Cuando se corta o los datos de la copia de una aplicación, los datos se almacenan en el portapapeles que se utilizará posteriormente en las operaciones de pegar.  Estos datos están en una variedad de formatos.  Cuando el usuario elige para pegar datos del portapapeles, la aplicación puede elegir cuál de estos formatos a utilizar.  La aplicación debe escribir para elegir el formato que proporciona la mayoría de la información, a menos que el usuario solicita específicamente un formato, utilizando el Pegado especial.  Antes de continuar, puede desear leer los temas de [Objetos de datos y orígenes de datos \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) .  Describe los fundamentos de cómo funcionan las transferencias de datos, y cómo implementarlos en las aplicaciones.  
  
 Windows define varios formatos estándar que se pueden utilizar para transferir datos a través del portapapeles.  Estos incluyen metarchivos, texto, mapas de bits, y otros.  OLE define varios formatos OLE\-específicos, también.  Para las aplicaciones que necesitan más detalles que proporcionado por estos formatos estándar, es recomendable registrar sus propios formatos de Portapapeles personalizados.  Utilice la función [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) de la API Win32 para ello.  
  
 Por ejemplo, Microsoft Excel registra un formato personalizado para las hojas de cálculo.  Este formato tarda mucho más información que, por ejemplo, hace un mapa de bits.  Cuando estos datos se pega en una aplicación que admite el formato de la hoja de cálculo, todas las fórmulas y valores de la hoja de cálculo se conservan y se pueden actualizar en caso necesario.  Microsoft Excel también coloca los datos en el portapapeles en formatos para que pueda pegar como elemento.  Cualquier contenedor OLE de documento puede pegar esta información como elemento incrustado.  Este elemento incrustado se puede cambiar utilizando Microsoft Excel.  El portapapeles también contiene un mapa de bits simple del intervalo seleccionado en la hoja de cálculo.  Esto también se puede pegar en contenedores de OLE del documento o en editores bitmap, como paint.  En el caso de un mapa de bits, sin embargo, no hay forma de manipular los datos como una hoja de cálculo.  
  
 Para recuperar el la máxima información del portapapeles, las aplicaciones deben comprobar estos formatos personalizados antes de pegar datos del portapapeles.  
  
 Por ejemplo, para habilitar el comando cortar, puede escribir a controlador algo parecido a:  
  
 [!code-cpp[NVC_MFCListView#3](../mfc/codesnippet/CPP/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Copiando y pegando datos](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)  
  
-   [Utilizar el Portapapeles de Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [Objetos de datos de OLE y orígenes de datos y transferencia de datos uniforme](../mfc/data-objects-and-data-sources-ole.md)  
  
## Vea también  
 [Portapapeles](../mfc/clipboard.md)