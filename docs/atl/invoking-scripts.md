---
title: Invocar Scripts (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
ms.openlocfilehash: 6ca744ced53677550e7b77f44d4f6550da744372
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820565"
---
# <a name="invoking-scripts"></a>Invocar Scripts

[Usar parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) se tratan los mapas de reemplazo y una referencia al método **AddReplacement**. El registrador tiene otros ocho métodos específicos para secuencias de comandos, y todos se describen en la tabla siguiente.

|Método|Descripción de la sintaxis /|
|------------|-------------------------|
|**ResourceRegister**|**HRESULT ResourceRegister( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType` **);**<br /><br /> Registra el script contenido en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *nID* y *szType* contienen el identificador del recurso y el tipo, respectivamente.|
|**ResourceUnregister**|**HRESULT ResourceUnregister( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType` **);**<br /><br /> Anula el registro de la secuencia de comandos contenida en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *nID* y *szType* contienen el identificador del recurso y el tipo, respectivamente.|
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType` **);**<br /><br /> Registra el script contenido en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *NID* y *szType* contienen el identificador de cadena y el tipo, el recurso respectivamente.|
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType` **);**<br /><br /> Anula el registro de la secuencia de comandos contenida en un recurso del módulo. *resFileName* indica la ruta de acceso UNC en el mismo módulo. *NID* y *szType* contienen el identificador de cadena y el tipo, el recurso respectivamente.|
|**FileRegister**|**HRESULT FileRegister( LPCOLESTR**  *fileName*  **);**<br /><br /> Registra el script en un archivo. *nombre de archivo* es una ruta de acceso UNC a un archivo que contiene un script de recursos (o es).|
|**FileUnregister**|**HRESULT FileUnregister( LPCOLESTR**  *fileName*  **);**<br /><br /> Anula el registro de la secuencia de comandos en un archivo. *nombre de archivo* es una ruta de acceso UNC a un archivo que contiene un script de recursos (o es).|
|**StringRegister**|**HRESULT StringRegister( LPCOLESTR**  *data*  **);**<br /><br /> Registra el script en una cadena. *datos* contiene la secuencia de comandos.|
|**StringUnregister**|**HRESULT StringUnregister( LPCOLESTR**  *data*  **);**<br /><br /> Anula el registro de la secuencia de comandos en una cadena. *datos* contiene la secuencia de comandos.|

**ResourceRegisterSz** y **ResourceUnregisterSz**, son similares a **ResourceRegister** y **ResourceUnregister**, pero le permiten especificar una cadena identificador.

Los métodos **FileRegister** y **FileUnregister** son útiles si no desea que la secuencia de comandos en un recurso o si desea que la secuencia de comandos en su propio archivo. Los métodos **StringRegister** y **StringUnregister** permiten almacenar el archivo que se almacenará en una cadena asignada dinámicamente.

## <a name="see-also"></a>Vea también

[Crear scripts del registrador](../atl/creating-registrar-scripts.md)
