GEOJSON
============

Go package to easy and quick create datastructure which can be serialized to geojson format

INSTALATION
---------------------

>`go get https://github.com/kpawlik/geojson`
>`go install https://github.com/kpawlik/geojson`

USAGE EXAMPLE
---------------------


    package main

    import (
        "fmt"
        gj "github.com/kpawlik/geojson"
    )

    func main() {
        var (
            f *gj.Feature
        )
        // feature
        p := gj.NewPoint(gj.Coordinate{12, 3.123})
        f = gj.NewFeature(p, nil, nil)
        if gjstr, err := gj.Marshal(f); err != nil {
            panic(err)
        } else {
            fmt.Println(gjstr)
        }
        // feature with propertises
        props := map[string]interface{}{"name": "location", "code": 107}
        f = gj.NewFeature(p, props, nil)
        if gjstr, err := gj.Marshal(f); err != nil {
            panic(err)
        } else {
            fmt.Println(gjstr)
        }
        // feature with propertises and id
        f = gj.NewFeature(p, props, 11101)
        if gjstr, err := gj.Marshal(f); err != nil {
            panic(err)
        } else {
            fmt.Println(gjstr)
        }
        ls := gj.NewLineString(gj.Coordinates{{1, 1}, {2.001, 3}, {4001, 1223}})
        f = gj.NewFeature(ls, nil, nil)
        if gjstr, err := gj.Marshal(f); err != nil {
            panic(err)
        } else {
            fmt.Println(gjstr)
        }

    }
