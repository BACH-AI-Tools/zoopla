# Zoopla MCP Server

English | [简体中文](./README.md) | [繁體中文](./README_ZH-TW.md)

## 🚀 Quick Start with EMCP Platform

**[EMCP](https://sit-emcp.kaleido.guru)** is a powerful MCP server management platform that allows you to quickly use various MCP servers without manual configuration!

### Quick Start:

1. 🌐 Visit **[EMCP Platform](https://sit-emcp.kaleido.guru)**
2. 📝 Register and login
3. 🎯 Go to **MCP Marketplace** to browse all available MCP servers
4. 🔍 Search or find this server (`bach-zoopla`)
5. 🎉 Click the **"Install MCP"** button
6. ✅ Done! You can now use it in your applications

### EMCP Platform Advantages:

- ✨ **Zero Configuration**: No need to manually edit config files
- 🎨 **Visual Management**: Easy-to-use GUI for managing all MCP servers
- 🔐 **Secure & Reliable**: Centralized API key and authentication management
- 🚀 **One-Click Install**: Rich selection of servers in MCP Marketplace
- 📊 **Usage Statistics**: Real-time service call monitoring

Visit **[EMCP Platform](https://sit-emcp.kaleido.guru)** now to start your MCP journey!


---

## Introduction

This is an automatically generated MCP server using [FastMCP](https://fastmcp.wiki) for accessing the Zoopla API.

- **PyPI Package**: `bach-zoopla`
- **Version**: 1.0.0
- **Transport Protocol**: stdio


## 安装

### 从 PyPI 安装:

```bash
pip install bach-zoopla
```

### 从源码安装:

```bash
pip install -e .
```

## 运行

### 方式 1: 使用 uvx（推荐，无需安装）

```bash
# 运行（uvx 会自动安装并运行）
uvx --from bach-zoopla bach_zoopla

# 或指定版本
uvx --from bach-zoopla@latest bach_zoopla
```

### 方式 2: 直接运行（开发模式）

```bash
python server.py
```

### 方式 3: 安装后作为命令运行

```bash
# 安装
pip install bach-zoopla

# 运行（命令名使用下划线）
bach_zoopla
```

## Configuration

### API Authentication

This API requires authentication. Please set environment variable:

```bash
export API_KEY="your_api_key_here"
```

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `API_KEY` | API Key | Yes |




### 在 Claude Desktop 中使用

编辑 Claude Desktop 配置文件 `claude_desktop_config.json`:


```json
{
  "mcpServers": {
    "zoopla": {
      "command": "python",
      "args": ["E:\path\to\zoopla\server.py"],
      "env": {
        "API_KEY": "your_api_key_here"
      }
    }
  }
}
```

**Note**: Replace `E:\path\to\zoopla\server.py` with the actual server file path.


## 可用工具

此服务器提供以下工具:


### `propertiesv2list`

List properties for sale or rent with options and filters

**端点**: `GET /properties/v2/list`


**参数**:

- `locationValue` (string) *必需*: The value of geoLabel field returned in .../v2/auto-complete endpoint with listings as search_type. Or the value of name field returned in .../house-prices/v2/get-area (If you are searching by postal code). You must use EXACTLY the value returned by the endpoint. *'listing_id' OR 'area' parameter must be provided to get this endpoint working.

- `locationIdentifier` (string) *必需*: The value of geoIdentifier field returned in .../v2/auto-complete endpoint with listings as search_type. Or the value of id field returned in ..../house-prices/v2/get-area endpoint (If you are searching by postal code). You must use EXACTLY the value returned by the endpoint.

- `category` (string): One of the following residential|commercial

- `furnishedState` (string): One of the following : Any|furnished|part_furnished|unfurnished

- `includeRented` (string): Example value: 

- `includeRetirementHomes` (string): Example value: 

- `includeSharedAccommodation` (string): Example value: 

- `includeSharedOwnership` (string): Example value: 

- `includeSold` (string): Example value: 

- `isAuction` (string): Example value: 

- `petsAllowed` (string): Example value: 

- `billsIncluded` (string): Example value: 

- `keywords` (string): Any word or term, ex : garden,wooden floors

- `section` (string): One of the following : for-sale|to-rent

- `bedsMax` (string): Max number of bed rooms (1 - 10)

- `bedsMin` (string): Min number of bed rooms (1 - 10)

- `priceMax` (string): Maximum sale or rent price

- `priceMin` (string): Minimum sale or rent price

- `sortOrder` (string): One of the following : newest_listings|highest_price|lowest_price|most_reduced

- `page` (string): The page index for paging purpose

- `radius` (string): The radius (miles) to look for properties (0.25 - 40)

- `priceFrequency` (string): One of the following per_month|per_year

- `newHomes` (string): One of the following : only|exclude

- `added` (string): Recently added. One of the following : 24_hours|3_days|7_days|14_days|30_days

- `propertySubType` (string): Filter properties by category. Ignore OR one of the followings (Separated by comma for multiple options) : park_home,bungalow,farms_land,terraced,flats,semi_detached,detached

- `chainFree` (string): Example value: 

- `reducedPriceOnly` (string): Example value: 

- `feature` (string): One of the followings : has_balcony_terrace|has_parking_garage|has_garden . Separated by comma for multiple options. Ex : has_balcony_terrace,has_parking_garage,...

- `tenure` (string): One of the followings : share_of_freehold|freehold|leasehold. Ex : freehold,leasehold,...

- `smartTags` (string): One of the followings : condition.needs_modernisation|architecture.period_property|type.cottage|style.modern|attributes.utility_room|attributes.basement|attributes.conservatory|attributes.home_office|attributes.bath|attributes.en_suite|attributes.patio|attributes.kitchen_island. Ex : condition.needs_modernisation,architecture.period_property,...



---


### `house_pricesv2estimate`

Returned list of estimated house prices

**端点**: `GET /house-prices/v2/estimate`


**参数**:

- `geoIdentifier` (string) *必需*: The value of 'urlPath' field returned in .../house-prices/v2/auto-complete endpoint OR the value of 'id' field returned in .../house-prices/v2/get-area endpoint.

- `after` (string): The offset to ignore for paging purpose.

- `first` (string): The number of items per response



---


### `agentsdetail`

Get detailed information of an agent by id

**端点**: `GET /agents/detail`


**参数**:

- `id` (string) *必需*: The value of id field returned in .../agents/list endpoint



---


### `agentslist`

List agents with filters and options

**端点**: `GET /agents/list`


**参数**:

- `location` (string) *必需*: The value of geoIdentifier field returned in .../v2/auto-complete endpoint with listings as search_type. Or the value of id field returned in ..../house-prices/v2/get-area endpoint (If you are searching by postal code). You must use EXACTLY the value returned by the endpoint.

- `search_type` (string): One of the followings : estate-agents|letting-agents|commercial-agents

- `company_name` (string): Search by agent name. Either 'location' or 'company_name' is required. You can ignore 'location' parameter when passing value into 'company_name' parameter.

- `agents_sort` (string): One of the following : a_z|lowest_avg_price|highest_avg_price|shortest_avg_age|longest_avg_age

- `pn` (string): The page index for paging purpose

- `radius` (string): The radius (miles) to look for agents (0.25 - 40)



---


### `house_pricesget_area_stats_deprecated`

Get area stats

**端点**: `GET /house-prices/get-area-stats`


**参数**:

- `property_id` (string) *必需*: The value of property_id field returned in .../house-prices/estimate endpoint.



---


### `house_pricesget_historic_listings_deprecated`

Get historic listings

**端点**: `GET /house-prices/get-historic-listings`


**参数**:

- `property_id` (string) *必需*: The value of property_id field returned in .../house-prices/estimate endpoint.



---


### `house_pricesv2get_area`

Use along with .../house-prices/v2/auto-complete endpoint to get related geo id. For example, geo id of postal code.

**端点**: `GET /house-prices/v2/get-area`


**参数**:

- `geoString` (string) *必需*: Postal code, city, district, ward, area, etc.... Use exact values returned in .../house-prices/v2/auto-complete endpoint for best result



---


### `house_pricesget_running_costs_deprecated`

Get running costs

**端点**: `GET /house-prices/get-running-costs`


**参数**:

- `property_id` (string) *必需*: The value of property_id field returned in .../house-prices/estimate endpoint.



---


### `house_pricesget_market_activity_deprecated`

Get market activity in an area

**端点**: `GET /house-prices/get-market-activity`


**参数**:

- `identifier` (string): The value of suggestions/identifier json object returned in .../auto-complete endpoint with properties as search_type. You must use EXACTLY the value returned by the endpoint.

- `area` (string) *必需*: The value of suggestions/value json object returned in .../auto-complete endpoint with properties as search_type. You must use EXACTLY the value returned by the endpoint.



---


### `house_pricesget_sales_history_deprecated`

Get sales history

**端点**: `GET /house-prices/get-sales-history`


**参数**:

- `property_id` (string) *必需*: The value of property_id field returned in .../house-prices/estimate endpoint.



---


### `propertiesget_nearby_deprecated`

Get nearest points of interest

**端点**: `GET /properties/get-nearby`


**参数**:

- `listing_id` (string) *必需*: The value of listing_id field returned in .../properties/list endpoint



---


### `propertiesv2detail`

Get property detail

**端点**: `GET /properties/v2/detail`


**参数**:

- `listingId` (string) *必需*: The value of listingId field returned in .../properties/v2/list endpoint



---


### `propertiesget_broadband_deprecated`

Get broadband information

**端点**: `GET /properties/get-broadband`


**参数**:

- `listing_id` (string) *必需*: The value of listing_id field returned in .../properties/list endpoint



---


### `propertiesget_running_costs_deprecated`

Get running costs

**端点**: `GET /properties/get-running-costs`


**参数**:

- `listing_id` (string) *必需*: The value of listing_id field returned in .../properties/list endpoint

- `category` (string): One of the following residential|commercial

- `section` (string): One of the following for-sale|to-rent



---


### `propertieslist_deprecated`

List properties for sale or rent with options and filters

**端点**: `GET /properties/list`


**参数**:

- `area` (string) *必需*: The value of suggestions/value json object returned in .../auto-complete endpoint with listings as search_type. You must use EXACTLY the value returned by the endpoint. *'listing_id' OR 'area' parameter must be provided to get this endpoint working.

- `identifier` (string): The value of suggestions/identifier json object returned in .../auto-complete endpoint with listings as search_type. You must use EXACTLY the value returned by the endpoint.

- `listing_id` (string): The value of listing_id field returned right in this endpoint. *'listing_id' OR 'area' parameter must be provided to get this endpoint working.

- `category` (string): One of the following residential|commercial

- `created_since` (string): The date time from which properties added. The format must be yyyy-MM-dd HH:mm:ss, Ex : 2020-09-16 15:00:00

- `furnished` (string): One of the following furnished|part_furnished|unfurnished

- `include_featured_properties` (string): One of the following 1 | 0

- `include_rented` (string): One of the following 1 | 0

- `include_retirement_homes` (string): One of the following yes | no

- `include_shared_accommodation` (string): One of the following yes | no

- `include_shared_ownership` (string): One of the following yes | no

- `include_sold` (string): One of the following 1 | 0

- `keywords` (string): Any word or term, ex : garden,wooden floors

- `listing_status` (string): One of the following sale | rent

- `maximum_beds` (string): Max number of bed rooms (1 - 10)

- `minimum_beds` (string): Min number of bed rooms (1 - 10)

- `maximum_price` (string): Maximum sale or rent price

- `minimum_price` (string): Minimum sale or rent price

- `order_by` (string): One of the following age|price|price_change|view_count

- `ordering` (string): One of the following ascending|descending

- `page_number` (string): The page index for paging purpose

- `page_size` (string): The number of items per response (max 40)

- `property_type` (string): One of the following and separated by comma for multiple values : flats|farms_land|terraced|semi_detached|detached|bungalow|park_home|offices|retail|industrial|hospitality|land

- `radius` (string): The radius (miles) to look for properties (1 - 40)

- `pets_allowed` (string): One of the following yes | no

- `price_frequency` (string): One of the following per_month|per_year

- `step_back_used` (string): One of the following 1 | 0

- `bills_included` (string): One of the following yes | no

- `floor_area_max` (string): Maximum floor area, only use with commercial category.

- `floor_area_min` (string): Minimum floor area, only use with commercial category.

- `floor_area_units` (string): One of the following sq_feet|sq_metres

- `new_homes` (string): One of the following yes | no



---


### `propertiesget_area_stats_deprecated`

Get area stats

**端点**: `GET /properties/get-area-stats`


**参数**:

- `listing_id` (string) *必需*: The value of listing_id field returned in .../properties/list endpoint



---


### `v2auto_complete`

Get auto complete suggestion by term or phrase

**端点**: `GET /v2/auto-complete`


**参数**:

- `locationPrefix` (string) *必需*: Example value: greenwich



---


### `auto_complete_deprecated`

Get auto complete suggestion by term or phrase

**端点**: `GET /auto-complete`


**参数**:

- `search_term` (string) *必需*: Example value: greenwich

- `search_type` (string): One of the following properties|listings. Use listings value to get suggestion for .../properties/list endpoint. Use properties value to get suggestion for .../house-prices/estimate endpoint.



---


### `house_pricesv2detail`

Get property price detailed information

**端点**: `GET /house-prices/v2/detail`


**参数**:

- `uprn` (string) *必需*: The value of "uprn" field returned in .../house-prices/v2/estimate endpoint.



---


### `house_pricesv2auto_complete`

Get suggestions by term or phrase about city, country, area,etc...

**端点**: `GET /house-prices/v2/auto-complete`


**参数**:

- `addressPartial` (string) *必需*: City, district, ward, area, etc....



---


### `house_pricesget_points_of_interest_deprecated`

Get nearest points of interest

**端点**: `GET /house-prices/get-points-of-interest`


**参数**:

- `property_id` (string) *必需*: The value of property_id field returned in .../house-prices/estimate endpoint.



---


### `house_pricesestimate_deprecated`

Returned list of estimated house prices

**端点**: `GET /house-prices/estimate`


**参数**:

- `identifier` (string): The value of suggestions/identifier json object returned in .../auto-complete endpoint with properties as search_type. You must use EXACTLY the value returned by the endpoint.

- `area` (string) *必需*: The value of suggestions/value json object returned in .../auto-complete endpoint with properties as search_type. You must use EXACTLY the value returned by the endpoint.

- `order_by` (string): One of the following price_paid|last_sold|address|estimated_value

- `ordering` (string): One of the following ascending|descending

- `page_number` (string): The page index for paging purpose

- `page_size` (string): The number of items per response (max 40)

- `property_type` (string): One of the following detached|flat|terraced|semi_detached



---



## 技术栈

- **FastMCP**: 快速、Pythonic 的 MCP 服务器框架
- **传输协议**: stdio
- **HTTP 客户端**: httpx

## 开发

This server is automatically generated by [API-to-MCP](https://github.com/BACH-AI-Tools/api-to-mcp) tool.

Version: 1.0.0
