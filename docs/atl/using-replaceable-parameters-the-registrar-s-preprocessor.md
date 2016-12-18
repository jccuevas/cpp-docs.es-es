---
title: "Using Replaceable Parameters (The Registrar&#39;s Preprocessor) | Microsoft Docs"
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
  - "AddReplacement"
  - "ClearReplacements"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "%MODULE%"
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using Replaceable Parameters (The Registrar&#39;s Preprocessor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los parámetros reemplazables permiten al cliente de un registro especifique datos en tiempo de ejecución.  Para ello, el registro mantiene un reemplazo asignado en la que escribe los valores asociados con los parámetros reemplazables en el script.  El registro crea estas entradas en tiempo de ejecución.  
  
##  <a name="_atl_using_.25.module.25"></a> Mediante el %MODULE%  
 [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) automáticamente genera un script que utilice `%MODULE%`.  ATL utiliza este parámetro reemplazable para la ubicación real de DLL o EXE del servidor.  
  
## Concatenar datos en tiempo de ejecución con datos de script  
 Otro uso de preprocesador es concatenar datos en tiempo de ejecución con datos del script.  Por ejemplo, supongamos que una entrada es necesaria que contiene una ruta de acceso completa a un módulo con la cadena “`, 1`” anexado al final.  Primero, defina la siguiente extensión:  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 A continuación, antes de llamar a uno de los métodos de procesamiento de script enumerados en [Invocar scripts](../atl/invoking-scripts.md), agregue un reemplazo al mapa:  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/CPP/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 Durante el análisis de script, el registro expanda `'%MODULE%, 1'` a `c:\mycode\mydll.dll, 1`.  
  
> [!NOTE]
>  En un script de registro, 4K es el tamaño máximo de token.  \(El símbolo consiste en cualquier elemento reconocible en la sintaxis.\) Esto incluye los tokenes creados o expandidos por el preprocesador.  
  
> [!NOTE]
>  Sustituir valores de reemplazo en tiempo de ejecución, quite la llamada en el script a la macro de [DECLARE\_REGISTRY\_RESOURCE](../Topic/DECLARE_REGISTRY_RESOURCE.md) o de [DECLARE\_REGISTRY\_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md) .  En su lugar, sustitúyalo con su propio método de `UpdateRegistry` que llame a [CAtlModule::UpdateRegistryFromResourceD](../Topic/CAtlModule::UpdateRegistryFromResourceD.md) o [CAtlModule::UpdateRegistryFromResourceS](../Topic/CAtlModule::UpdateRegistryFromResourceS.md), y pase la matriz de estructuras de **\_ATL\_REGMAP\_ENTRY** .  La matriz de **\_ATL\_REGMAP\_ENTRY** debe tener una entrada que se establezca {**NULL**,**NULL**}, y esta entrada debe ser siempre la última entrada.  Si no, un error de infracción de acceso se generará cuando se llama a **UpdateRegistryFromResource** .  
  
> [!NOTE]
>  Al compilar un proyecto que genera un archivo ejecutable, ATL agrega automáticamente comillas alrededor del nombre de ruta creado en tiempo de ejecución con el parámetro de script de registro de **%MODULE%** .  Si no desea que el nombre de ruta para incluir las comillas, utilice el nuevo parámetro de **%MODULE\_RAW%** en su lugar.  
>   
>  Al compilar un proyecto que genere un archivo DLL, ATL no agregará comillas al nombre de ruta si se utiliza **%MODULE%** o **%MODULE\_RAW%** .  
  
## Vea también  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)