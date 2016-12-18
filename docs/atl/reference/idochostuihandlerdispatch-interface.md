---
title: "IDocHostUIHandlerDispatch Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDocHostUIHandlerDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDocHostUIHandlerDispatch interface"
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDocHostUIHandlerDispatch Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una interfaz a Microsoft HTML que analiza y que genera el motor.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
interface IDocHostUIHandlerDispatch : IDispatch  
  
```  
  
## Members  
  
### Métodos públicos  
  
> [!NOTE]
>  Los vínculos de la siguiente tabla se a temas de referencia de INet SDK para los miembros de la interfaz de [IDocUIHostHandler](https://msdn.microsoft.com/en-us/library/aa753260.aspx) .  `IDocHostUIHandlerDispatch` tiene la misma funcionalidad que **IDocUIHostHandler**, con la diferencia siendo ese `IDocHostUIHandlerDispatch` es dispinterface mientras **IDocUIHostHandler** es una interfaz personalizada.  
  
|||  
|-|-|  
|[\<caps:sentence id\="tgt7" sentenceid\="bbafd0070a97938421603b1ef8409510" class\="tgtSentence"\>EnableModeless\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753253.aspx)|Denominado de implementación MSHTML de [IOleInPlaceActiveObject:: EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115).  También denominado cuando MSHTML muestra la interfaz de usuario modal.|  
|[\<caps:sentence id\="tgt10" sentenceid\="2cfbfb70fe0af79263134b694d06311c" class\="tgtSentence"\>FilterDataObject\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753254.aspx)|Llamada al host MSHTML por a permitir que el host reemplace el objeto de datos MSHTML.|  
|[\<caps:sentence id\="tgt12" sentenceid\="715255e2d7f611c97308a373328e19a0" class\="tgtSentence"\>GetDropTarget\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753255.aspx)|Llamado por MSHTML cuando se usa como destino para permitir que el host proporcione [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)alternativo.|  
|[\<caps:sentence id\="tgt14" sentenceid\="5a51a8633a0d2036f843073d6f35a4af" class\="tgtSentence"\>GetExternal\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753256.aspx)|Llamado por MSHTML para obtener la interfaz IDispatch host.|  
|[\<caps:sentence id\="tgt16" sentenceid\="ce27e0c2f7ebb0aaa2f9088818dc8347" class\="tgtSentence"\>GetHostInfo\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753257.aspx)|Recupera las funciones de la interfaz de usuario de host MSHTML.|  
|[\<caps:sentence id\="tgt18" sentenceid\="693bd2149b17c4586cdc167e13e59f0a" class\="tgtSentence"\>GetOptionKeyPath\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753258.aspx)|Devuelve la clave del Registro en la que almacena MSHTML preferencias del usuario.|  
|[\<caps:sentence id\="tgt20" sentenceid\="7fce94585b477684cc21a38fe9ee288c" class\="tgtSentence"\>HideUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753259.aspx)|Se invoca cuando MSHTML quita los menús y barras de herramientas.|  
|[\<caps:sentence id\="tgt22" sentenceid\="359e4dcbd80b962decf88ef02d66fe14" class\="tgtSentence"\>OnDocWindowActivate\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753261.aspx)|Denominado de implementación MSHTML de [IOleInPlaceActiveObject:: OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281).|  
|[\<caps:sentence id\="tgt24" sentenceid\="8e472d7f3f3064d2ee6fdddd83002b86" class\="tgtSentence"\>OnFrameWindowActivate\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753262.aspx)|Denominado de implementación MSHTML de [IOleInPlaceActiveObject:: OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969).|  
|[\<caps:sentence id\="tgt26" sentenceid\="3fd38deec5e9f4201074e886bfb178a5" class\="tgtSentence"\>ResizeBorder\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753263.aspx)|Denominado de implementación MSHTML de [IOleInPlaceActiveObject:: ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053).|  
|[\<caps:sentence id\="tgt28" sentenceid\="2f382ba3de5494d18b20ccfa348f795e" class\="tgtSentence"\>ShowContextMenu\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753264.aspx)|Denominado MSHTML para mostrar un menú contextual.|  
|[\<caps:sentence id\="tgt30" sentenceid\="c6978c4c8ab30ae8380439da613bb63c" class\="tgtSentence"\>ShowUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753265.aspx)|Permite al host reemplace menús y barras de herramientas MSHTML.|  
|[\<caps:sentence id\="tgt32" sentenceid\="97bfd5aead25a2d9870b38da4b6745cd" class\="tgtSentence"\>TranslateAccelerator\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753266.aspx)|Llamado por MSHTML cuando se llama a [IOleInPlaceActiveObject:: TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) o [IOleControlSite:: TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) .|  
|[\<caps:sentence id\="tgt34" sentenceid\="55c20a6fb6b05f6059d72b2854a7d7e2" class\="tgtSentence"\>TranslateUrl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753267.aspx)|Llamado por MSHTML para permitir hospedar una oportunidad de modificar la dirección URL que se va a cargar.|  
|[\<caps:sentence id\="tgt36" sentenceid\="8fdf7c2c3ebf5fa12ecc909279c951ff" class\="tgtSentence"\>UpdateUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753268.aspx)|Notifica al host que el estado de comando ha cambiado.|  
  
## Comentarios  
 Un host puede reemplazar los menús, barras de herramientas, y menús contextuales utilizados por Microsoft HTML analizar y generar el motor \(MSHTML\) si implementa esta interfaz.  
  
## Requisitos  
 La definición de esta interfaz está disponible como IDL o C\+\+, como se muestra a continuación.  
  
|Tipo de definición|Archivo|  
|------------------------|-------------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(también incluido en ATLBase.h\)|  
  
## Vea también  
 [IDocUIHostHandler](https://msdn.microsoft.com/en-us/library/aa753260.aspx)