---
title: Invocar secuencias de comandos (ATL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StringRegister
dev_langs:
- C++
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cbf969f601bd90e84bf0ee15ae2ea3dcb392610
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="invoking-scripts"></a>Invocar secuencias de comandos
[Usar parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) se tratan los mapas de reemplazo y una referencia al método **AddReplacement**. El registrador tiene otros ocho métodos específicos para secuencias de comandos y todos se describen en la tabla siguiente.  
  
|Método|Descripción de la sintaxis /|  
|------------|-------------------------|  
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Registra el script que contiene en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. `nID`y `szType` contienen el identificador y el tipo del recurso respectivamente.|  
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Anula el registro de la secuencia de comandos incluido en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. `nID`y `szType` contienen el identificador y el tipo del recurso respectivamente.|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***NID* **, LPCOLESTR** `szType` **);** <br /><br /> Registra el script que contiene en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *NID* y `szType` contienen el identificador de cadena y el tipo, el recurso respectivamente.|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***NID* **, LPCOLESTR** `szType` **);** <br /><br /> Anula el registro de la secuencia de comandos incluido en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *NID* y `szType` contienen el identificador de cadena y el tipo, el recurso respectivamente.|  
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***);** <br /><br /> Registra el script en un archivo. *nombre de archivo* es una ruta de acceso UNC a un archivo que contiene un script de recursos (o es).|  
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***fileName***);** <br /><br /> Anula el registro de la secuencia de comandos en un archivo. *nombre de archivo* es una ruta de acceso UNC a un archivo que contiene un script de recursos (o es).|  
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***datos***);** <br /><br /> Registra el script en una cadena. *datos* contiene la secuencia de comandos.|  
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***datos***);** <br /><br /> Anula el registro de la secuencia de comandos en una cadena. *datos* contiene la secuencia de comandos.|  
  
 **ResourceRegisterSz** y **ResourceUnregisterSz**, son similares a **ResourceRegister** y **ResourceUnregister**, pero le permiten especificar un identificador de cadena.  
  
 Los métodos **FileRegister** y **FileUnregister** son útiles si no desea que la secuencia de comandos en un recurso o si desea que la secuencia de comandos en su propio archivo. Los métodos **StringRegister** y **StringUnregister** permiten almacenar el archivo que se almacena en una cadena asignada dinámicamente.  
  
## <a name="see-also"></a>Vea también  
 [Crear scripts del registrador](../atl/creating-registrar-scripts.md)

