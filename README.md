## Macでも同じようにキーバインド設定できるよ！
先に[キーバインドソフトで幸せになるWindows、AHK編](https://qiita.com/bambooRake/items/dbcd15d670c9b4a55a2f)
という記事を挙げた。
Windowsと同じくFキーにマウス左ボタンを割り当ててる。ここ数年でトラックパッドの巨大化によって誤タッチも増え、使い難さはあるがマウスよりは全然はかどる！

## マウス以外にもなんか教えてよ！
前回記事ではマウスの左ボタンを割り当てると幸せになれるということに終始したが、他にもおすすめ設定はもちろんある。

## 移動系１
- かなキー＋h,j,k,l。vim風の移動割り当て。

## 移動系２
- かなキー＋a,e。これはemacs風に行頭・行末。

## 削除系
- かなキー＋x,d。これはvim風。macはfn+delete(?最近使ってないから忘れたcmdだっけ)使わないといけなかったりするから。winでいうとxにbs,dにdelを割り当ててる。

## 注意点
これらの機能を実現するには、[Karabiner-Elements](https://github.com/tekezo/Karabiner-Elements)というソフトを使う。
ただ注意点としてWindowsのAHK程柔軟な処理はさせられない。それもこれもMacOSがEl Capitanあたりでセキュリティが上がって、前身のKarabinerというソフトが動作しなくなってしまったからだ。
Karabinerはとっても良く出来る子だったのよ
(´;ω;｀)

## 設定を晒す。
前身のKarabinerの時には、commandキーにoptionキーを割り当てて置いて、commandキー＋TABキーの時だけはカスタマイズ動作ではなくアプリスイッチャーを動作させるだとか、かなキー＋Kキーで行末までカット（Emacs風に）とか出来てたんだけどなぁ。（後者はelementsでもできるけど移行しきれてない。）

```json

{
    "title": "Mouse Personal rules (@bamboo).",
    "rules": [
        {
            "description": "英数キーをユーザ修飾キーに（helpで代替）",
            "manipulators": [
                {
                    "type": "basic",
                    "from": {
                        "key_code": "help",
                        "modifiers": {
                            "optional": [ "any" ]
                        }
                    },
                    "to": [
                    {
                        "set_variable": {
                        "name": "press_help",
                        "value": 1
                        }
                    }
                    ],
                    "to_after_key_up": [
                    {
                        "set_variable": {
                        "name": "press_help",
                        "value": 0
                        }
                    }
                    ]
                },
                {
                    "type": "basic",
                    "from": {
                        "key_code": "f",
                        "modifiers": {
                            "optional": [ "any" ]
                        }
                    },
                    "to": [
                        { "pointing_button": "button1" }
                    ],
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ]
                },
                {
                    "type": "basic",
                    "from": {
                        "key_code": "v",
                        "modifiers": {
                            "optional": [ "any" ]
                        }
                    },
                    "to": [
                        { "pointing_button": "button2" }
                    ],
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ]
                },
                {
                    "type": "basic",
                    "from": {
                        "key_code": "g",
                        "modifiers": {
                            "optional": [ "any" ]
                        }
                    },
                    "to": [
                        { "pointing_button": "button3" }
                    ],
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ]
                },
                {
                    "type": "basic",
                    "from": {
                        "key_code": "r",
                        "modifiers": {
                            "optional": [ "any" ]
                        }
                    },
                    "to": [
                        {
                            "mouse_key": {
                            "vertical_wheel": -30
                            }
                        }
                    ],
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ]
                },
                {
                    "type": "basic",
                    "from": {
                        "key_code": "4",
                        "modifiers": {
                            "optional": [ "any" ]
                        }
                    },
                    "to": [
                        {
                            "mouse_key": {
                            "vertical_wheel": 30
                            }
                        }
                    ],
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ]
                },
                {
                    "type": "basic",
                    "from": {
                        "key_code": "t",
                        "modifiers": {
                            "optional": [ "any" ]
                        }
                    },
                    "to": [
                        {
                            "mouse_key": {
                            "horizontal_wheel": 30
                            }
                        }
                    ],
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ]
                },
                {
                    "type": "basic",
                    "from": {
                        "key_code": "5",
                        "modifiers": {
                            "optional": [ "any" ]
                        }
                    },
                    "to": [
                        {
                            "mouse_key": {
                            "horizontal_wheel": -30
                            }
                        }
                    ],
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "h",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "left_arrow"
                        }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "j",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "down_arrow"
                        }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "k",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "up_arrow"
                        }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "l",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "right_arrow"
                        }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "x",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "delete_or_backspace"
                        }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "d",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "delete_forward"
                        }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "s",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "return_or_enter"
                        }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "a",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "a",
                            "modifiers": [
                                "control"
                            ]
                        }
                    ]
                },
                {
                    "type": "basic",
                    "conditions": [
                      {
                        "type": "variable_if",
                        "name": "press_help",
                        "value": 1
                      }
                    ],
                    "from": {
                        "key_code": "e",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "e",
                            "modifiers": [
                                "control"
                            ]
                        }
                    ]
                },
                {
                    "conditions": [
                        {
                            "name": "press_help",
                            "type": "variable_if",
                            "value": 1
                        }
                    ],
                    "from": {
                        "key_code": "tab",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "tab",
                            "modifiers": [
                                "command"
                            ]
                        }
                    ],
                    "type": "basic"
                },
                {
                    "conditions": [
                        {
                            "name": "press_help",
                            "type": "variable_if",
                            "value": 1
                        }
                    ],
                    "from": {
                        "key_code": "q",
                        "modifiers": {
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "q",
                            "modifiers": [
                                "command"
                            ]
                        }
                    ],
                    "type": "basic"
                },
                {
                    "from": {
                        "key_code": "q",
                        "modifiers": {
                            "mandatory": [
                                "command"
                            ],
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "",
                            "modifiers": [
                                "command"
                            ]
                        }
                    ],
                    "type": "basic"
                }

            ]
        },
        {
            "description": "Change Command+Tab to Control+Tab",
            "manipulators": [
                {
                    "from": {
                        "key_code": "tab",
                        "modifiers": {
                            "mandatory": [
                                "command"
                            ],
                            "optional": [
                                "any"
                            ]
                        }
                    },
                    "to": [
                        {
                            "key_code": "tab",
                            "modifiers": [
                                "control"
                            ]
                        }
                    ],
                    "type": "basic"
                }
            ]
        }
    ]
}

```
elementsが開発段階ということもあり、自分の設定も既存のマウス設定用のJSONファイルを拡張し続けていて整理できてない。マウスの設定の中に他の設定が混在しまくり…

## 最後に
今回は、サラッと書き流した。
elementsは開発は続けられていて、前身のソフトよりも良くなってる点もあり、とても楽しみにしている。ただ、機能は前身のものをカバーしきれていない。
短押し→直接入力、長押し→日本語入力とか切り替えられるようになりたいよー




