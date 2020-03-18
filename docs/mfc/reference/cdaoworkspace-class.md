---
title: CDaoWorkspace (clase)
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: c1d235035cee9342c8c54c7aaa4e05a96d5a37e3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425974"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace (clase)

Administra una sesión de base de datos con nombre, protegida mediante contraseña de inicio de sesión a cierre de sesión, por un único usuario. DAO es compatible con Office 2013. DAO 3,6 es la versión final y se considera obsoleta.

## <a name="syntax"></a>Sintaxis

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoWorkspace:: CDaoWorkspace](#cdaoworkspace)|Construye un objeto de área de trabajo. Después, llame a `Create` o `Open`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoWorkspace:: Append](#append)|Anexa un área de trabajo recién creada a la colección de áreas de trabajo del motor de base de datos.|
|[CDaoWorkspace:: BeginTrans](#begintrans)|Comienza una nueva transacción, que se aplica a todas las bases de datos abiertas en el área de trabajo.|
|[CDaoWorkspace:: Close](#close)|Cierra el área de trabajo y todos los objetos que contiene. Las transacciones pendientes se revierten.|
|[CDaoWorkspace:: CommitTrans](#committrans)|Completa la transacción actual y guarda los cambios.|
|[CDaoWorkspace:: CompactDatabase](#compactdatabase)|Compacta (o duplica) una base de datos.|
|[CDaoWorkspace:: Create](#create)|Crea un nuevo objeto de área de trabajo de DAO.|
|[CDaoWorkspace:: GetDatabaseCount](#getdatabasecount)|Devuelve el número de objetos de base de datos DAO en la colección de bases de datos del área de trabajo.|
|[CDaoWorkspace:: GetDatabaseInfo](#getdatabaseinfo)|Devuelve información sobre una base de datos DAO especificada definida en la colección de bases de datos del área de trabajo.|
|[CDaoWorkspace:: GetIniPath](#getinipath)|Devuelve la ubicación de la configuración de inicialización del motor de base de datos de Microsoft Jet en el registro de Windows.|
|[CDaoWorkspace:: GetIsolateODBCTrans](#getisolateodbctrans)|Devuelve un valor que indica si varias transacciones que implican el mismo origen de datos ODBC están aisladas a través de varias conexiones forzadas al origen de datos.|
|[CDaoWorkspace:: GetLoginTimeout](#getlogintimeout)|Devuelve el número de segundos antes de que se produzca un error cuando el usuario intenta iniciar sesión en una base de datos ODBC.|
|[CDaoWorkspace:: GetName](#getname)|Devuelve el nombre definido por el usuario para el objeto de área de trabajo.|
|[CDaoWorkspace:: GetUserName](#getusername)|Devuelve el nombre de usuario especificado cuando se creó el área de trabajo. Este es el nombre del propietario del área de trabajo.|
|[CDaoWorkspace:: GetVersion](#getversion)|Devuelve una cadena que contiene la versión del motor de base de datos asociada con el área de trabajo.|
|[CDaoWorkspace:: GetWorkspaceCount](#getworkspacecount)|Devuelve el número de objetos de área de trabajo DAO en la colección de áreas de trabajo del motor de base de datos.|
|[CDaoWorkspace:: GetWorkspaceInfo](#getworkspaceinfo)|Devuelve información sobre un área de trabajo DAO especificada definida en la colección de áreas de trabajo del motor de base de datos.|
|[CDaoWorkspace:: idle](#idle)|Permite que el motor de base de datos realice tareas en segundo plano.|
|[CDaoWorkspace:: IsOpen](#isopen)|Devuelve un valor distinto de cero si el área de trabajo está abierta.|
|[CDaoWorkspace:: Open](#open)|Abre explícitamente un objeto de área de trabajo asociado al área de trabajo predeterminada de DAO.|
|[CDaoWorkspace:: RepairDatabase](#repairdatabase)|Intenta reparar una base de datos dañada.|
|[CDaoWorkspace:: Rollback](#rollback)|Finaliza la transacción actual y no guarda los cambios.|
|[CDaoWorkspace:: SetDefaultPassword](#setdefaultpassword)|Establece la contraseña que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin una contraseña específica.|
|[CDaoWorkspace:: SetDefaultUser](#setdefaultuser)|Establece el nombre de usuario que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin un nombre de usuario específico.|
|[CDaoWorkspace:: SetIniPath](#setinipath)|Establece la ubicación de la configuración de inicialización del motor de base de datos de Microsoft Jet en el registro de Windows.|
|[CDaoWorkspace:: SetIsolateODBCTrans](#setisolateodbctrans)|Especifica si varias transacciones que implican el mismo origen de datos ODBC están aisladas forzando varias conexiones con el origen de datos.|
|[CDaoWorkspace:: SetLoginTimeout](#setlogintimeout)|Establece el número de segundos antes de que se produzca un error cuando el usuario intenta iniciar sesión en un origen de datos ODBC.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoWorkspace:: m_pDAOWorkspace](#m_pdaoworkspace)|Apunta al objeto de área de trabajo DAO subyacente.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, no necesitará varias áreas de trabajo y no tendrá que crear objetos de área de trabajo explícitos; Cuando se abren objetos de base de datos y de conjunto de registros, se utiliza el área de trabajo predeterminada de DAO. Sin embargo, si es necesario, puede ejecutar varias sesiones a la vez mediante la creación de objetos de área de trabajo adicionales. Cada objeto de área de trabajo puede contener varios objetos de base de datos abiertos en su propia colección de bases de datos. En MFC, un área de trabajo es principalmente un administrador de transacciones, que especifica un conjunto de bases de datos abiertas en el mismo "espacio de transacciones".

> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Conectividad abierta de bases de datos (ODBC). Todos los nombres de clase de base de datos DAO tienen un prefijo "CDao". En general, las clases MFC basadas en DAO son más capaces que las clases MFC basadas en ODBC. Las clases basadas en DAO obtienen acceso a los datos a través del motor de base de datos de Microsoft Jet, incluidos los controladores ODBC. También admiten operaciones de lenguaje de definición de datos (DDL), como la creación de bases de datos y la adición de tablas y campos a través de las clases, sin tener que llamar a DAO directamente.

## <a name="capabilities"></a>Capacidades

La `CDaoWorkspace` de clase proporciona lo siguiente:

- Acceso explícito, si es necesario, a un área de trabajo predeterminada, que se crea al inicializar el motor de base de datos. Normalmente, se usa el área de trabajo predeterminada de DAO implícitamente mediante la creación de objetos de base de datos y de conjunto de registros.

- Espacio de transacciones en el que las transacciones se aplican a todas las bases de datos abiertas en el área de trabajo. Puede crear áreas de trabajo adicionales para administrar espacios de transacciones independientes.

- Una interfaz a muchas propiedades del motor de base de datos de Microsoft Jet subyacente (vea las funciones miembro estáticas). Abrir o crear un área de trabajo, o llamar a una función miembro estática antes de abrir o crear, inicializa el motor de base de datos.

- Acceso a la colección de áreas de trabajo del motor de base de datos, que almacena todas las áreas de trabajo activas que se han anexado a ella. También puede crear y trabajar con áreas de trabajo sin anexarlas a la colección.

## <a name="security"></a>Seguridad

MFC no implementa las colecciones Users y Groups en DAO, que se usan para el control de seguridad. Si necesita esos aspectos de DAO, debe programarlos personalmente a través de llamadas directas a interfaces de DAO. Para obtener más información, consulte la [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Uso

Puede utilizar la `CDaoWorkspace` de clase para:

- Abra explícitamente el área de trabajo predeterminada.

   Normalmente, el uso del área de trabajo predeterminada es implícito, cuando se abren nuevos objetos [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Sin embargo, puede que necesite tener acceso de forma explícita; por ejemplo, para tener acceso a las propiedades del motor de base de datos o a la colección de áreas de trabajo. Vea "uso implícito del área de trabajo predeterminada" a continuación.

- Cree nuevas áreas de trabajo. Llame a [Append](#append) si desea agregarlos a la colección de áreas de trabajo.

- Abra un área de trabajo existente en la colección de áreas de trabajo.

La creación de una nueva área de trabajo que aún no existe en la colección de áreas de trabajo se describe en la función miembro [Create](#create) . Los objetos del área de trabajo no se conservan de ninguna manera entre sesiones del motor de datababase. Si la aplicación vincula MFC estáticamente, al finalizar la aplicación se desinicializa el motor de base de datos. Si la aplicación se vincula con MFC dinámicamente, el motor de base de datos no se inicializa cuando se descarga el archivo DLL de MFC.

Abrir explícitamente el área de trabajo predeterminada o abrir un área de trabajo existente en la colección de áreas de trabajo se describe en la función miembro [abierta](#open) .

Finalizar una sesión de área de trabajo cerrando el área de trabajo con la función miembro [Close](#close) . `Close` cierra las bases de datos que no se han cerrado previamente y revierte las transacciones no confirmadas.

## <a name="transactions"></a>Transacciones

DAO administra las transacciones en el nivel de área de trabajo; por lo tanto, las transacciones en un área de trabajo con varias bases de datos abiertas se aplican a todas las bases de datos. Por ejemplo, si dos bases de datos tienen actualizaciones sin confirmar y llama a [CommitTrans](#committrans), se confirman todas las actualizaciones. Si desea limitar las transacciones a una sola base de datos, necesita un objeto de área de trabajo independiente para ella.

## <a name="implicit-use-of-the-default-workspace"></a>Uso implícito del área de trabajo predeterminada

MFC usa el área de trabajo predeterminada de DAO implícitamente en las siguientes circunstancias:

- Si crea un nuevo objeto `CDaoDatabase` pero no lo hace a través de un objeto `CDaoWorkspace` existente, MFC crea automáticamente un objeto de área de trabajo temporal, que corresponde al área de trabajo predeterminada de DAO. Si lo hace para varias bases de datos, todos los objetos de base de datos se asocian al área de trabajo predeterminada. Puede tener acceso al área de trabajo de una base de datos a través de un miembro de datos de `CDaoDatabase`.

- Del mismo modo, si crea un objeto de `CDaoRecordset` sin proporcionar un puntero a un objeto `CDaoDatabase`, MFC crea un objeto de base de datos temporal y, por extensión, un objeto de área de trabajo temporal. Puede tener acceso a la base de datos de un conjunto de registros e indirectamente su área de trabajo a través de un miembro de datos de `CDaoRecordset`.

## <a name="other-operations"></a>Otras operaciones

También se proporcionan otras operaciones de base de datos, como reparar una base de datos dañada o compactar una base de datos.

Para obtener información sobre cómo llamar directamente a DAO y sobre la seguridad de DAO, vea la [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

##  <a name="append"></a>CDaoWorkspace:: Append

Llame a esta función miembro después de llamar a [Create](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Observaciones

`Append` anexa un objeto de área de trabajo recién creado a la colección de áreas de trabajo del motor de base de datos. Las áreas de trabajo no se conservan entre las sesiones del motor de base de datos; solo se almacenan en la memoria, no en el disco. No es necesario anexar un área de trabajo; Si no es así, puede utilizarlo.

Un área de trabajo anexada permanece en la colección de áreas de trabajo, en un estado activo abierto, hasta que se llama a la función miembro [Close](#close) .

Para obtener información relacionada, vea el tema sobre el método Append en la ayuda de DAO.

##  <a name="begintrans"></a>CDaoWorkspace:: BeginTrans

Llame a esta función miembro para iniciar una transacción.

```
void BeginTrans();
```

### <a name="remarks"></a>Observaciones

Después de llamar a `BeginTrans`, las actualizaciones realizadas en los datos o en la estructura de la base de datos surtirán efecto cuando se confirme la transacción. Dado que el área de trabajo define un solo espacio de transacción, la transacción se aplica a todas las bases de datos abiertas en el área de trabajo. Hay dos formas de completar la transacción:

- Llame a la función miembro [CommitTrans](#committrans) para confirmar la transacción y guardar los cambios en el origen de datos.

- O bien, llame a la función miembro [Rollback](#rollback) para cancelar la transacción.

Al cerrar el objeto de área de trabajo o un objeto de base de datos mientras una transacción está pendiente, se revierten todas las transacciones pendientes.

Si necesita aislar las transacciones en un origen de datos ODBC de los de otro origen de datos ODBC, vea la función miembro [SetIsolateODBCTrans](#setisolateodbctrans) .

##  <a name="cdaoworkspace"></a>CDaoWorkspace:: CDaoWorkspace

Construye un objeto `CDaoWorkspace`.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Observaciones

Después de construir el C++ objeto, tiene dos opciones:

- Llame a la función miembro [abierta](#open) del objeto para abrir el área de trabajo predeterminada o para abrir un objeto existente en la colección de áreas de trabajo.

- O bien, llame a la función miembro [Create](#create) del objeto para crear un nuevo objeto de área de trabajo DAO. Esto inicia explícitamente una nueva sesión de área de trabajo, a la que se puede hacer referencia a través del objeto `CDaoWorkspace`. Después de llamar a `Create`, puede llamar a [Append](#append) si desea agregar el área de trabajo a la colección de áreas de trabajo del motor de base de datos.

Vea la información general de la clase para [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) para obtener información sobre Cuándo es necesario crear explícitamente un objeto `CDaoWorkspace`. Normalmente, se usan áreas de trabajo creadas implícitamente al abrir un objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) sin especificar un área de trabajo o al abrir un objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) sin especificar un objeto de base de datos. Los objetos DAO de MFC creados de esta manera utilizan el área de trabajo predeterminada de DAO, que se crea una vez y se reutiliza.

Para liberar un área de trabajo y sus objetos contenidos, llame a la función miembro [Close](#close) del objeto del área de trabajo.

##  <a name="close"></a>CDaoWorkspace:: Close

Llame a esta función miembro para cerrar el objeto de área de trabajo.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Al cerrar un objeto de área de trabajo abierta, se libera el objeto DAO subyacente y, si el área de trabajo es un miembro de la colección de áreas de trabajo, se quita de la colección. Llamar a `Close` es una buena práctica de programación.

> [!CAUTION]
>  Al cerrar un objeto de área de trabajo se cierra cualquier base de datos abierta en el área de trabajo. Esto hace que los conjuntos de registros abiertos en las bases de datos se cierren también y que se reviertan todas las modificaciones o actualizaciones pendientes. Para obtener información relacionada, vea las funciones miembro [CDaoDatabase:: Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset:: Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef:: Close](../../mfc/reference/cdaotabledef-class.md#close)y [CDaoQueryDef:: Close](../../mfc/reference/cdaoquerydef-class.md#close) .

Los objetos del área de trabajo no son permanentes; solo existen mientras existan referencias a ellos. Esto significa que cuando finaliza la sesión del motor de base de datos, el área de trabajo y su colección de bases de datos no se conservan. Debe volver a crearlos para la siguiente sesión; para ello, abra el área de trabajo y las bases de datos de nuevo.

Para obtener información relacionada, vea el tema sobre el método Close en la ayuda de DAO.

##  <a name="committrans"></a>CDaoWorkspace:: CommitTrans

Llame a esta función miembro para confirmar una transacción: Guarde un grupo de ediciones y actualizaciones en una o varias bases de datos en el área de trabajo.

```
void CommitTrans();
```

### <a name="remarks"></a>Observaciones

Una transacción se compone de una serie de cambios en los datos de la base de datos o en su estructura, comenzando por una llamada a [BeginTrans](#begintrans). Cuando finalice la transacción, puede confirmarla o revertirla (cancelar los cambios) con la [reversión](#rollback). De forma predeterminada, sin transacciones, las actualizaciones de los registros se confirman inmediatamente. La llamada a `BeginTrans` provoca el retraso de las actualizaciones hasta que se llama a `CommitTrans`.

> [!CAUTION]
>  Dentro de un área de trabajo, las transacciones siempre son globales en el área de trabajo y no se limitan a una base de datos o un conjunto de registros. Si realiza operaciones en más de una base de datos o en un conjunto de registros dentro de una transacción de área de trabajo, `CommitTrans` confirma todas las actualizaciones pendientes y `Rollback` restaura todas las operaciones en esas bases de datos y conjuntos de registros.

Al cerrar una base de datos o un área de trabajo con transacciones pendientes, se revierten todas las transacciones.

> [!NOTE]
>  No se trata de un mecanismo de confirmación en dos fases. Si no se puede confirmar una actualización, otras todavía se confirmarán.

##  <a name="compactdatabase"></a>CDaoWorkspace:: CompactDatabase

Llame a esta función miembro para compactar un determinado Microsoft Jet (. MDB).

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszSrcName*<br/>
Nombre de una base de datos cerrada existente. Puede ser una ruta de acceso completa y un nombre de archivo, como "C:\\\MYDB. MDB ". Si el nombre de archivo tiene una extensión, debe especificarla. Si la red es compatible con la Convención de nomenclatura universal (UNC), también puede especificar una ruta de acceso de red, como "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ". (Se necesitan barras diagonales inversas dobles en las cadenas de ruta de acceso porque C++ "\\" es el carácter de escape).

*lpszDestName*<br/>
La ruta de acceso completa de la base de datos compactada que está creando. También puede especificar una ruta de acceso de red como con *lpszSrcName*. No se puede usar el argumento *lpszDestName* para especificar el mismo archivo de base de datos que *lpszSrcName*.

*lpszPassword*<br/>
Una contraseña que se utiliza cuando se desea compactar una base de datos protegida por contraseña. Tenga en cuenta que si usa la versión de `CompactDatabase` que toma una contraseña, debe proporcionar todos los parámetros. Además, dado que se trata de un parámetro de conexión, requiere un formato especial, como se indica a continuación: PWD = *lpszPassword*. Por ejemplo:; PWD = "feliz". (Se requiere el punto y coma inicial).

*lpszLocale*<br/>
Expresión de cadena que se usa para especificar el orden de intercalación para la creación de *lpszDestName*. Si omite este argumento aceptando el valor predeterminado de `dbLangGeneral` (vea a continuación), la configuración regional de la nueva base de datos es la misma que la de la base de datos anterior. Los valores posibles son:

- `dbLangGeneral` inglés, alemán, Francés, Portugués, Italiano y español moderno

- `dbLangArabic` Árabe

- `dbLangCyrillic` Ruso

- `dbLangCzech` Checo

- `dbLangDutch` holandés

- `dbLangGreek` griego

- `dbLangHebrew` hebreo

- `dbLangHungarian` Húngaro

- `dbLangIcelandic` islandés

- `dbLangNordic` idiomas nórdicos (solo la versión 1,0 del motor de base de datos de Microsoft Jet)

- `dbLangNorwdan` noruego y danés

- `dbLangPolish` Polaco

- `dbLangSpanish` español tradicional

- `dbLangSwedfin` sueco y Finés

- `dbLangTurkish` Turco

*nOptions*<br/>
Indica una o más opciones para la base de datos de destino, *lpszDestName*. Si omite este argumento aceptando el valor predeterminado, *lpszDestName* tendrá el mismo cifrado y la misma versión que *lpszSrcName*. Puede combinar la opción `dbEncrypt` o `dbDecrypt` con una de las opciones de versión mediante el operador OR bit a bit. Los valores posibles, que especifican un formato de base de datos, no una versión del motor de base de datos, son:

- `dbEncrypt` cifrar la base de datos durante la compactación.

- `dbDecrypt` descifrar la base de datos durante la compactación.

- `dbVersion10` crear una base de datos que use el motor de base de datos de Microsoft Jet versión 1,0 durante la compactación.

- `dbVersion11` crear una base de datos que use el motor de base de datos de Microsoft Jet versión 1,1 durante la compactación.

- `dbVersion20` crear una base de datos que use el motor de base de datos de Microsoft Jet versión 2,0 durante la compactación.

- `dbVersion30` crear una base de datos que use el motor de base de datos de Microsoft Jet versión 3,0 durante la compactación.

Puede usar `dbEncrypt` o `dbDecrypt` en el argumento Options para especificar si se va a cifrar o descifrar la base de datos a medida que se compacta. Si omite una constante de cifrado o si incluye `dbDecrypt` y `dbEncrypt`, *lpszDestName* tendrá el mismo cifrado que *lpszSrcName*. Puede utilizar una de las constantes de versión del argumento Options para especificar la versión del formato de datos para la base de datos compactada. Esta constante afecta solo a la versión del formato de datos de *lpszDestName*. Solo puede especificar una constante de versión. Si omite una constante de versión, *lpszDestName* tendrá la misma versión que *lpszSrcName*. Solo puede compactar *lpszDestName* en una versión que sea igual o posterior a la de *lpszSrcName*.

> [!CAUTION]
>  Si una base de datos no está cifrada, es posible, incluso si implementa la seguridad de usuario/contraseña, para leer directamente el archivo de disco binario que constituye la base de datos.

### <a name="remarks"></a>Observaciones

A medida que cambia los datos en una base de datos, el archivo de base de datos se puede fragmentar y utilizar más espacio en disco del necesario. Periódicamente, debe compactar la base de datos para desfragmentar el archivo de base de datos. La base de datos compactada suele ser más pequeña. También puede optar por cambiar el orden de intercalación, el cifrado o la versión del formato de datos al copiar y compactar la base de datos.

> [!CAUTION]
>  La función miembro `CompactDatabase` no convertirá correctamente una base de datos de Microsoft Access completa de una versión a otra. Solo se convierte el formato de datos. Los objetos definidos por Microsoft Access, como formularios e informes, no se convierten. Sin embargo, los datos se convierten correctamente.

> [!TIP]
>  También puede usar `CompactDatabase` para copiar un archivo de base de datos.

Para obtener más información acerca de la compactación de bases de datos, vea el tema "método CompactDatabase" en la ayuda de DAO.

##  <a name="create"></a>CDaoWorkspace:: Create

Llame a esta función miembro para crear un nuevo objeto de área de trabajo DAO y asociarlo al objeto de `CDaoWorkspace` MFC.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Cadena con un máximo de 14 caracteres que nombra de forma única el nuevo objeto de área de trabajo. Debe proporcionar un nombre. Para obtener información relacionada, vea el tema "propiedad de nombre" en la ayuda de DAO.

*lpszUserName*<br/>
El nombre de usuario del propietario del área de trabajo. Para conocer los requisitos, vea el parámetro *lpszDefaultUser* para la función miembro [SetDefaultUser](#setdefaultuser) . Para obtener información relacionada, vea el tema "propiedad UserName" en la ayuda de DAO.

*lpszPassword*<br/>
Contraseña del nuevo objeto de área de trabajo. Una contraseña puede tener una longitud de hasta 14 caracteres y puede contener cualquier carácter excepto ASCII 0 (NULL). En las contraseñas se distingue entre mayúsculas y minúsculas. Para obtener información relacionada, vea el tema "propiedad de contraseña" en la ayuda de DAO.

### <a name="remarks"></a>Observaciones

El proceso de creación general es:

1. Construya un objeto [CDaoWorkspace](#cdaoworkspace) .

1. Llame a la función miembro `Create` del objeto para crear el área de trabajo DAO subyacente. Debe especificar un nombre de área de trabajo.

1. Opcionalmente, llame a [Append](#append) si desea agregar el área de trabajo a la colección de áreas de trabajo del motor de base de datos. Puede trabajar con el área de trabajo sin anexarla.

Después de la llamada a `Create`, el objeto de área de trabajo se encuentra en un estado abierto y listo para su uso. No llame a `Open` después de `Create`. No llame a `Create` si el área de trabajo ya existe en la colección de áreas de trabajo. `Create` inicializa el motor de base de datos si aún no se ha inicializado para la aplicación.

##  <a name="getdatabasecount"></a>CDaoWorkspace:: GetDatabaseCount

Llame a esta función miembro para recuperar el número de objetos de base de datos DAO en la colección de bases de datos del área de trabajo, el número de bases de datos abiertas en el área de trabajo.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Valor devuelto

El número de bases de datos abiertas en el área de trabajo.

### <a name="remarks"></a>Observaciones

`GetDatabaseCount` resulta útil si necesita recorrer en bucle todas las bases de datos definidas en la colección de bases de datos del área de trabajo. Para obtener información sobre una base de datos determinada de la colección, vea [GetDatabaseInfo](#getdatabaseinfo). El uso típico es llamar a `GetDatabaseCount` para el número de bases de datos abiertas y, a continuación, usar ese número como índice de bucle para las llamadas repetidas a `GetDatabaseInfo`.

##  <a name="getdatabaseinfo"></a>CDaoWorkspace:: GetDatabaseInfo

Llame a esta función miembro para obtener distintos tipos de información sobre una base de datos abierta en el área de trabajo.

```
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del objeto Database de la colección de bases de datos del área de trabajo, para la búsqueda por índice.

*dbinfo*<br/>
Referencia a un objeto [cdaodatabaseinfo (](../../mfc/reference/cdaodatabaseinfo-structure.md) que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican la información sobre la base de datos que se va a recuperar. Aquí se enumeran las opciones disponibles junto con lo que hacen que la función devuelva:

- AFX_DAO_PRIMARY_INFO (valor predeterminado) nombre, actualizable, transacciones

- AFX_DAO_SECONDARY_INFO información principal más: versión, orden de intercalación, tiempo de espera de consulta

- AFX_DAO_ALL_INFO información principal y secundaria más: conectar

*lpszName*<br/>
Nombre del objeto de base de datos, para la búsqueda por nombre. El nombre es una cadena con un máximo de 14 caracteres que nombra de forma única el nuevo objeto de área de trabajo.

### <a name="remarks"></a>Observaciones

Una versión de la función permite buscar una base de datos por índice. La otra versión permite buscar una base de datos por nombre.

Para obtener una descripción de la información que se devuelve en *dbinfo*, consulte la estructura [cdaodatabaseinfo (](../../mfc/reference/cdaodatabaseinfo-structure.md) . Esta estructura tiene miembros que corresponden a los elementos de la información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, también se obtiene información sobre cualquier nivel anterior.

##  <a name="getinipath"></a>CDaoWorkspace:: GetIniPath

Llame a esta función miembro para obtener la ubicación de la configuración de inicialización del motor de base de datos de Microsoft Jet en el registro de Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Valor devuelto

Un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la ubicación del registro.

### <a name="remarks"></a>Observaciones

Puede usar la ubicación para obtener información acerca de la configuración del motor de base de datos. La información devuelta es en realidad el nombre de una subclave del registro.

Para obtener información relacionada, vea los temas "propiedad IniPath" y "personalizar la configuración del registro de Windows para el acceso a datos" en la ayuda de DAO.

##  <a name="getisolateodbctrans"></a>CDaoWorkspace:: GetIsolateODBCTrans

Llame a esta función miembro para obtener el valor actual de la propiedad IsolateODBCTrans de DAO para el área de trabajo.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si las transacciones ODBC están aisladas; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

En algunas situaciones, puede que necesite tener varias transacciones simultáneas pendientes en la misma base de datos ODBC. Para ello, debe abrir un área de trabajo independiente para cada transacción. Tenga en cuenta que aunque cada área de trabajo puede tener su propia conexión ODBC a la base de datos, esto ralentiza el rendimiento del sistema. Dado que el aislamiento de transacción no suele ser necesario, las conexiones ODBC de varios objetos de área de trabajo abiertas por el mismo usuario se comparten de forma predeterminada.

Algunos servidores ODBC, como Microsoft SQL Server, no permiten transacciones simultáneas en una sola conexión. Si necesita tener más de una transacción a la vez pendiente de dicha base de datos, establezca la propiedad IsolateODBCTrans en TRUE en cada área de trabajo en cuanto se abra. Esto fuerza una conexión ODBC independiente para cada área de trabajo.

Para obtener información relacionada, vea el tema "propiedad IsolateODBCTrans" en la ayuda de DAO.

##  <a name="getlogintimeout"></a>CDaoWorkspace:: GetLoginTimeout

Llame a esta función miembro para obtener el valor actual de la propiedad LoginTimeout de DAO para el área de trabajo.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Valor devuelto

El número de segundos antes de que se produzca un error al intentar iniciar sesión en una base de datos ODBC.

### <a name="remarks"></a>Observaciones

Este valor representa el número de segundos antes de que se produzca un error al intentar iniciar sesión en una base de datos ODBC. El valor LoginTimeout predeterminado es de 20 segundos. Cuando LoginTimeout se establece en 0, no se produce ningún tiempo de espera y la comunicación con el origen de datos puede dejar de responder.

Cuando intenta iniciar sesión en una base de datos ODBC, como Microsoft SQL Server, puede producirse un error en la conexión como resultado de errores de red o porque el servidor no se está ejecutando. En lugar de esperar que los 20 segundos predeterminados se conecten, puede especificar cuánto tiempo espera el motor de base de datos antes de que se produzca un error. El inicio de sesión en el servidor se produce implícitamente como parte de varios eventos diferentes, como la ejecución de una consulta en una base de datos de servidor externo.

Para obtener información relacionada, vea el tema "propiedad LoginTimeout" en la ayuda de DAO.

##  <a name="getname"></a>CDaoWorkspace:: GetName

Llame a esta función miembro para obtener el nombre definido por el usuario del objeto de área de trabajo DAO subyacente al objeto `CDaoWorkspace`.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

[CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre definido por el usuario del objeto de área de trabajo DAO.

### <a name="remarks"></a>Observaciones

El nombre es útil para tener acceso al objeto de área de trabajo DAO en la colección de áreas de trabajo del motor de base de datos por nombre.

Para obtener información relacionada, vea el tema "propiedad de nombre" en la ayuda de DAO.

##  <a name="getusername"></a>CDaoWorkspace:: GetUserName

Llame a esta función miembro para obtener el nombre del propietario del área de trabajo.

```
CString GetUserName();
```

### <a name="return-value"></a>Valor devuelto

[CString](../../atl-mfc-shared/reference/cstringt-class.md) que representa el propietario del objeto de área de trabajo.

### <a name="remarks"></a>Observaciones

Para obtener o establecer los permisos para el propietario del área de trabajo, llame a DAO directamente para comprobar la configuración de la propiedad Permissions; Esto determina los permisos que tiene el usuario. Para trabajar con permisos, necesita un sistema. Archivo MDA.

Para obtener información sobre cómo llamar directamente a DAO, vea la [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Para obtener información relacionada, vea el tema "propiedad UserName" en la ayuda de DAO.

##  <a name="getversion"></a>CDaoWorkspace:: GetVersion

Llame a esta función miembro para determinar la versión del motor de base de datos de Microsoft Jet en uso.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Valor devuelto

[CString](../../atl-mfc-shared/reference/cstringt-class.md) que indica la versión del motor de base de datos asociada al objeto.

### <a name="remarks"></a>Observaciones

El valor devuelto representa el número de versión con el formato "Major. minor"; por ejemplo, "3,0". El número de versión del producto (por ejemplo, 3,0) consta del número de versión (3), un punto y el número de versión (0).

Para obtener información relacionada, vea el tema "propiedad version" en la ayuda de DAO.

##  <a name="getworkspacecount"></a>CDaoWorkspace:: GetWorkspaceCount

Llame a esta función miembro para recuperar el número de objetos del área de trabajo DAO en la colección de áreas de trabajo del motor de base de datos.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Valor devuelto

El número de áreas de trabajo abiertas en la colección de áreas de trabajo.

### <a name="remarks"></a>Observaciones

Este recuento no incluye ninguna área de trabajo abierta que no se anexe a la colección. `GetWorkspaceCount` resulta útil si necesita recorrer todas las áreas de trabajo definidas en la colección de áreas de trabajo. Para obtener información sobre un área de trabajo determinada en la colección, vea [GetWorkspaceInfo](#getworkspaceinfo). El uso típico consiste en llamar a `GetWorkspaceCount` para el número de áreas de trabajo abiertas y, a continuación, usar ese número como índice de bucle para llamadas repetidas a `GetWorkspaceInfo`.

##  <a name="getworkspaceinfo"></a>CDaoWorkspace:: GetWorkspaceInfo

Llame a esta función miembro para obtener distintos tipos de información sobre un área de trabajo abierta en la sesión.

```
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del objeto de base de datos de la colección de áreas de trabajo, para la búsqueda por índice.

*wkspcinfo*<br/>
Referencia a un objeto [cdaoworkspaceinfo (](../../mfc/reference/cdaoworkspaceinfo-structure.md) que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican la información sobre el área de trabajo que se va a recuperar. Aquí se enumeran las opciones disponibles junto con lo que hacen que la función devuelva:

- Nombre de AFX_DAO_PRIMARY_INFO (valor predeterminado)

- AFX_DAO_SECONDARY_INFO información principal más: nombre de usuario

- AFX_DAO_ALL_INFO información principal y secundaria más: aislar ODBCTrans

*lpszName*<br/>
Nombre del objeto de área de trabajo, para la búsqueda por nombre. El nombre es una cadena con un máximo de 14 caracteres que nombra de forma única el nuevo objeto de área de trabajo.

### <a name="remarks"></a>Observaciones

Para obtener una descripción de la información que se devuelve en *wkspcinfo*, consulte la estructura [cdaoworkspaceinfo (](../../mfc/reference/cdaoworkspaceinfo-structure.md) . Esta estructura tiene miembros que corresponden a los elementos de la información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, también se obtiene información de los niveles anteriores.

##  <a name="idle"></a>CDaoWorkspace:: idle

Llame a `Idle` para proporcionar al motor de base de datos la oportunidad de realizar tareas en segundo plano que pueden no estar actualizadas debido al procesamiento intensivo de datos.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parámetros

*nAcción*<br/>
Acción que se va a realizar durante el procesamiento inactivo. Actualmente, la única acción válida es `dbFreeLocks`.

### <a name="remarks"></a>Observaciones

Esto suele ser cierto en entornos multitarea de multiusuario en los que no hay tiempo de procesamiento en segundo plano suficiente para mantener actualizados todos los registros de un conjunto de registros.

> [!NOTE]
>  La llamada a `Idle` no es necesaria con las bases de datos creadas con la versión 3,0 del motor de base de datos de Microsoft Jet. Use `Idle` solo para bases de datos creadas con versiones anteriores.

Normalmente, se quitan los bloqueos de lectura y los datos de los objetos de conjunto de registros de tipo Dynaset local solo se actualizan cuando no se están produciendo otras acciones (incluidos los movimientos del mouse). Si llama periódicamente a `Idle`, proporciona al motor de base de datos un tiempo para ponerse al día en las tareas de procesamiento en segundo plano mediante la liberación de bloqueos de lectura innecesarios. Si se especifica la constante `dbFreeLocks` como un argumento, se retrasa el procesamiento hasta que se liberen todos los bloqueos de lectura.

Esta función miembro no es necesaria en entornos de un solo usuario a menos que se ejecuten varias instancias de una aplicación. La función miembro `Idle` puede aumentar el rendimiento en un entorno multiusuario porque obliga al motor de base de datos a vaciar los datos en el disco, liberando bloqueos en la memoria. También puede liberar bloqueos de lectura haciendo que las operaciones formen parte de una transacción.

Para obtener información relacionada, vea el tema sobre el método idle en la ayuda de DAO.

##  <a name="isopen"></a>CDaoWorkspace:: IsOpen

Llame a esta función miembro para determinar si el objeto de `CDaoWorkspace` está abierto; es decir, si el objeto MFC ha sido inicializado por una llamada a [Open](#open) o por una llamada a [Create](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de área de trabajo está abierto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Puede llamar a cualquiera de las funciones miembro de un área de trabajo que se encuentra en un estado abierto.

##  <a name="m_pdaoworkspace"></a>CDaoWorkspace:: m_pDAOWorkspace

Puntero al objeto de área de trabajo DAO subyacente.

### <a name="remarks"></a>Observaciones

Utilice este miembro de datos si necesita acceso directo al objeto DAO subyacente. Puede llamar a las interfaces del objeto DAO a través de este puntero.

Para obtener información sobre cómo obtener acceso directamente a objetos DAO, vea la [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="open"></a>CDaoWorkspace:: Open

Abre explícitamente un objeto de área de trabajo asociado al área de trabajo predeterminada de DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre del objeto de área de trabajo DAO que se va a abrir: una cadena con un máximo de 14 caracteres que nombra el área de trabajo de forma única. Acepte el valor predeterminado NULL para abrir explícitamente el área de trabajo predeterminada. Para conocer los requisitos de nomenclatura, consulte el parámetro *lpszName* para [Create](#create). Para obtener información relacionada, vea el tema "propiedad de nombre" en la ayuda de DAO.

### <a name="remarks"></a>Observaciones

Después de construir un objeto de `CDaoWorkspace`, llame a esta función miembro para realizar una de las acciones siguientes:

- Abra explícitamente el área de trabajo predeterminada. Pase NULL para *lpszName*.

- Abra un objeto de `CDaoWorkspace` existente, un miembro de la colección de áreas de trabajo, por nombre. Pase un nombre válido para un objeto de área de trabajo existente.

`Open` coloca el objeto de área de trabajo en un estado abierto y también inicializa el motor de base de datos si aún no se ha inicializado para la aplicación.

Aunque muchas `CDaoWorkspace` funciones miembro solo se pueden llamar después de abrir el área de trabajo, las siguientes funciones miembro, que operan en el motor de base de datos, están disponibles C++ después de la construcción del objeto, pero antes de una llamada a `Open`:

||||
|-|-|-|
|[Creación](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Idle](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>CDaoWorkspace:: RepairDatabase

Llame a esta función miembro si necesita intentar reparar una base de datos dañada que tenga acceso al motor de base de datos de Microsoft Jet.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
La ruta de acceso y el nombre de archivo de un archivo de base de datos de Microsoft Jet Engine existente. Si omite la ruta de acceso, solo se busca en el directorio actual. Si el sistema admite la Convención de nomenclatura universal (UNC), también puede especificar una ruta de acceso de red, como: "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ". (Se necesitan barras diagonales inversas dobles en la cadena de ruta de acceso porque C++ "\\" es el carácter de escape).

### <a name="remarks"></a>Observaciones

Debe cerrar la base de datos especificada por *lpszName* antes de repararla. En un entorno multiusuario, otros usuarios no pueden tener *lpszName* abierto mientras lo repara. Si *lpszName* no está cerrado o no está disponible para uso exclusivo, se produce un error.

Esta función miembro intenta reparar una base de datos marcada como posiblemente dañada por una operación de escritura incompleta. Esto puede ocurrir si una aplicación que usa el motor de base de datos de Microsoft Jet se cierra de forma inesperada debido a un problema de hardware del equipo o un corte de energía. Si completa la operación y llama a la función miembro [Close](../../mfc/reference/cdaodatabase-class.md#close) o sale de la aplicación de la manera habitual, la base de datos no se marcará como posiblemente dañada.

> [!NOTE]
>  Después de reparar una base de datos, también es una buena idea compactarla con la función miembro [CompactDatabase](#compactdatabase) para desfragmentar el archivo y recuperar espacio en disco.

Para obtener más información acerca de la reparación de bases de datos, vea el tema "método RepairDatabase" en la ayuda de DAO.

##  <a name="rollback"></a>CDaoWorkspace:: Rollback

Llame a esta función miembro para finalizar la transacción actual y restaurar todas las bases de datos del área de trabajo a su condición antes de que se iniciara la transacción.

```
void Rollback();
```

### <a name="remarks"></a>Observaciones

> [!CAUTION]
>  Dentro de un objeto de área de trabajo, las transacciones siempre son globales en el área de trabajo y no se limitan a una base de datos o un conjunto de registros. Si realiza operaciones en más de una base de datos o en un conjunto de registros dentro de una transacción de área de trabajo, `Rollback` restaura todas las operaciones en todas las bases de datos y conjuntos de registros.

Si cierra un objeto de área de trabajo sin guardar ni revertir las transacciones pendientes, las transacciones se revierten automáticamente. Si llama a [CommitTrans](#committrans) o `Rollback` sin llamar primero a [BeginTrans](#begintrans), se produce un error.

> [!NOTE]
>  Cuando se inicia una transacción, el motor de base de datos registra sus operaciones en un archivo guardado en el directorio especificado por la variable de entorno TEMP en la estación de trabajo. Si el archivo de registro de transacciones agota el almacenamiento disponible en la unidad temporal, el motor de base de datos hará que MFC inicie una `CDaoException` (error de DAO 2004). En este momento, si llama a `CommitTrans`, se confirma un número indeterminado de operaciones, pero se pierden las operaciones incompletas restantes y la operación debe reiniciarse. La llamada a `Rollback` libera el registro de transacciones y revierte todas las operaciones de la transacción.

##  <a name="setdefaultpassword"></a>CDaoWorkspace:: SetDefaultPassword

Llame a esta función miembro para establecer la contraseña predeterminada que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin una contraseña específica.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszPassword*<br/>
La contraseña predeterminada. Una contraseña puede tener una longitud de hasta 14 caracteres y puede contener cualquier carácter excepto ASCII 0 (NULL). En las contraseñas se distingue entre mayúsculas y minúsculas.

### <a name="remarks"></a>Observaciones

La contraseña predeterminada que establezca se aplica a las nuevas áreas de trabajo que cree después de la llamada. Al crear áreas de trabajo posteriores, no es necesario especificar una contraseña en la llamada a [Create](#create) .

Para utilizar esta función miembro:

1. Construya un objeto de `CDaoWorkspace` pero no llame a `Create`.

1. Llame a `SetDefaultPassword` y, si lo desea, [SetDefaultUser](#setdefaultuser).

1. Llame a `Create` para este objeto de área de trabajo o a los subsiguientes, sin especificar una contraseña.

De forma predeterminada, la propiedad DefaultUser está establecida en "admin" y la propiedad DefaultPassword está establecida en una cadena vacía ("").

Para obtener más información sobre la seguridad, vea el tema "propiedad Permissions" en la ayuda de DAO. Para obtener información relacionada, vea los temas "DefaultPassword Property" y "DefaultUser Property" en la ayuda de DAO.

##  <a name="setdefaultuser"></a>CDaoWorkspace:: SetDefaultUser

Llame a esta función miembro para establecer el nombre de usuario predeterminado que el motor de base de datos utiliza cuando se crea un objeto de área de trabajo sin un nombre de usuario específico.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parámetros

*lpszDefaultUser*<br/>
Nombre del usuario predeterminado. Un nombre de usuario puede tener una longitud de 1-20 caracteres e incluir caracteres alfabéticos. caracteres acentuados, números, espacios y símbolos excepto: "(comillas),/(barra diagonal), \ (barra diagonal inversa), \[ \] (corchetes),: ( &#124; dos puntos), (barra vertical), \< (Signo menor que), > (signo mayor que), + (signo más), = (signo igual),; (punto y coma),, (coma), (signo de interrogación), \* (asterisco), espacios iniciales y caracteres de control (ASCII 00 a ASCII 31). Para obtener información relacionada, vea el tema "propiedad UserName" en la ayuda de DAO.

### <a name="remarks"></a>Observaciones

El nombre de usuario predeterminado que establezca se aplicará a las nuevas áreas de trabajo que cree después de la llamada. Al crear áreas de trabajo posteriores, no es necesario especificar un nombre de usuario en la llamada a [Create](#create) .

Para utilizar esta función miembro:

1. Construya un objeto de `CDaoWorkspace` pero no llame a `Create`.

1. Llame a `SetDefaultUser` y, si lo desea, [SetDefaultPassword](#setdefaultpassword).

1. Llame a `Create` para este objeto de área de trabajo o a los subsiguientes, sin especificar un nombre de usuario.

De forma predeterminada, la propiedad DefaultUser está establecida en "admin" y la propiedad DefaultPassword está establecida en una cadena vacía ("").

Para obtener información relacionada, vea los temas "propiedad DefaultUser" y "propiedad DefaultPassword" en la ayuda de DAO.

##  <a name="setinipath"></a>CDaoWorkspace:: SetIniPath

Llame a esta función miembro para especificar la ubicación de la configuración del registro de Windows para el motor de base de datos de Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parámetros

*lpszRegistrySubkey*<br/>
Cadena que contiene el nombre de una subclave del registro de Windows para la ubicación de la configuración del motor de base de datos de Microsoft Jet o los parámetros necesarios para las bases de datos ISAM instalables.

### <a name="remarks"></a>Observaciones

Llame a `SetIniPath` solo si necesita especificar una configuración especial. Para obtener más información, vea el tema "propiedad IniPath" en la ayuda de DAO.

> [!NOTE]
>  Llame a `SetIniPath` durante la instalación de la aplicación, no cuando se ejecute la aplicación. se debe llamar a `SetIniPath` antes de abrir cualquier área de trabajo, base de datos o conjunto de registros; de lo contrario, MFC produce una excepción.

Puede utilizar este mecanismo para configurar el motor de base de datos con los valores del registro proporcionados por el usuario. El ámbito de este atributo está limitado a la aplicación y no se puede cambiar sin necesidad de reiniciar la aplicación.

##  <a name="setisolateodbctrans"></a>CDaoWorkspace:: SetIsolateODBCTrans

Llame a esta función miembro para establecer el valor de la propiedad IsolateODBCTrans de DAO para el área de trabajo.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parámetros

*bIsolateODBCTrans*<br/>
Pase TRUE si desea iniciar el aislamiento de las transacciones ODBC. Pase FALSE si desea detener el aislamiento de las transacciones ODBC.

### <a name="remarks"></a>Observaciones

En algunas situaciones, puede que necesite tener varias transacciones simultáneas pendientes en la misma base de datos ODBC. Para ello, debe abrir un área de trabajo independiente para cada transacción. Aunque cada área de trabajo puede tener su propia conexión ODBC con la base de datos, esto ralentiza el rendimiento del sistema. Dado que el aislamiento de transacción no suele ser necesario, las conexiones ODBC de varios objetos de área de trabajo abiertas por el mismo usuario se comparten de forma predeterminada.

Algunos servidores ODBC, como Microsoft SQL Server, no permiten transacciones simultáneas en una sola conexión. Si necesita tener más de una transacción a la vez pendiente de dicha base de datos, establezca la propiedad IsolateODBCTrans en TRUE en cada área de trabajo en cuanto se abra. Esto fuerza una conexión ODBC independiente para cada área de trabajo.

##  <a name="setlogintimeout"></a>CDaoWorkspace:: SetLoginTimeout

Llame a esta función miembro para establecer el valor de la propiedad LoginTimeout de DAO para el área de trabajo.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parámetros

*nSeconds*<br/>
El número de segundos antes de que se produzca un error al intentar iniciar sesión en una base de datos ODBC.

### <a name="remarks"></a>Observaciones

Este valor representa el número de segundos antes de que se produzca un error al intentar iniciar sesión en una base de datos ODBC. El valor LoginTimeout predeterminado es de 20 segundos. Cuando LoginTimeout se establece en 0, no se produce ningún tiempo de espera y la comunicación con el origen de datos puede dejar de responder.

Cuando intenta iniciar sesión en una base de datos ODBC, como Microsoft SQL Server, puede producirse un error en la conexión como resultado de errores de red o porque el servidor no se está ejecutando. En lugar de esperar que los 20 segundos predeterminados se conecten, puede especificar cuánto tiempo espera el motor de base de datos antes de que se produzca un error. El inicio de sesión en el servidor se produce implícitamente como parte de varios eventos diferentes, como la ejecución de una consulta en una base de datos de servidor externo. El valor de tiempo de espera está determinado por la configuración actual de la propiedad LoginTimeout.

Para obtener información relacionada, vea el tema "propiedad LoginTimeout" en la ayuda de DAO.

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
