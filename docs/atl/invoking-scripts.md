---
title: Invocar Scripts (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- StringRegister
dev_langs:
- C++
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e5bc5572a88f3df94811c3628333c8697a539b2
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849374"
---
# <a name="invoking-scripts"></a>Invocar Scripts
[Usar parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) se tratan los mapas de reemplazo y una referencia al método **AddReplacement**. El registrador tiene otros ocho métodos específicos para secuencias de comandos, y todos se describen en la tabla siguiente.  
  
|Método|Descripción de la sintaxis /|  
|------------|-------------------------|  
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Registra el script contenido en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *nID* y *szType* contienen el identificador del recurso y el tipo, respectivamente.|  
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Anula el registro de la secuencia de comandos contenida en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *nID* y *szType* contienen el identificador del recurso y el tipo, respectivamente.|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***NID* **, LPCOLESTR** `szType` **);** <br /><br /> Registra el script contenido en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *NID* y *szType* contienen el identificador de cadena y el tipo, el recurso respectivamente.|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***NID* **, LPCOLESTR** `szType` **);** <br /><br /> Anula el registro de la secuencia de comandos contenida en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *NID* y *szType* contienen el identificador de cadena y el tipo, el recurso respectivamente.|  
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***);** <br /><br /> Registra el script en un archivo. *nombre de archivo* es una ruta de acceso UNC a un archivo que contiene un script de recursos (o es).|  
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***fileName***);** <br /><br /> Anula el registro de la secuencia de comandos en un archivo. *nombre de archivo* es una ruta de acceso UNC a un archivo que contiene un script de recursos (o es).|  
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***datos***);** <br /><br /> Registra el script en una cadena. *datos* contiene la secuencia de comandos.|  
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***datos***);** <br /><br /> Anula el registro de la secuencia de comandos en una cadena. *datos* contiene la secuencia de comandos.|  
  
 **ResourceRegisterSz** y **ResourceUnregisterSz**, son similares a **ResourceRegister** y **ResourceUnregister**, pero le permiten especificar una cadena identificador.  
  
 Los métodos **FileRegister** y **FileUnregister** son útiles si no desea que la secuencia de comandos en un recurso o si desea que la secuencia de comandos en su propio archivo. Los métodos **StringRegister** y **StringUnregister** permiten almacenar el archivo que se almacenará en una cadena asignada dinámicamente.  
  
## <a name="see-also"></a>Vea también  
 [Crear scripts del registrador](../atl/creating-registrar-scripts.md)

