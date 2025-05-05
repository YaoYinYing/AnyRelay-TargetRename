# AnyRelay-TargetRename

A simple GHA workflow to convert any proxy nodes into relay targets by rename them following the naming pattern of [AnyRelay](https://github.com/YaoYinYing/AnyRelay).

## Prerequisites

1. a valid node subscription
2. a rename string for the nodes. each of the substitutions must be quoted e.g.:

   ```text
   `美国@RelayTarget-美国``尼日利亚@RelayTarget-尼日利亚``土耳其@RelayTarget-土耳其``印度@RelayTarget-印度``巴西@RelayTarget-巴西``阿联酋@RelayTarget-阿联酋``俄罗斯@RelayTarget-俄罗斯``巴基斯坦@RelayTarget-巴基斯坦``缅甸@RelayTarget-缅甸``菲律宾@RelayTarget-菲律宾``柬埔寨@RelayTarget-柬埔寨`
   ```

3. a subconvert backend support round-robin strategy of node load balancing
4. a subconvert frontend to compose the converted url based on the above information.
5. a gist with a file named as `clash.yaml`. 
6. a github pat with solely `gist` scope.

## Setup the secrets

| Name | Value | Description |
| --- | --- | --- |
| `GIST_ID`|  `<gist id>` | The gist id of the clash.yaml file. |
| `GIST_PAT` | `<github pat>` | The github pat with solely `gist` scope. |
| `RELAY_TARGETS_URL` | `<compose subconvert url>` | The composed url from the subconvert frontend. |
| `USER_AGENT` |`mihomo.party/v1.7.3 (clash.meta)]`| The user agent used by wget to fetch the clash config. |

## Usage

1. fork this repo
2. compose the subconvert url, create a gist with a file named as `clash.yaml`, and a pat
3. fullfill the secrets
4. trigger the workflow
5. copy the raw url of generated gist file as the relay target input of `AnyRelay`.

