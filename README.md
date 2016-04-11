# Repository

class func get(url: String, params: [String: AnyObject]? = nil, complete: (result: AnyObject, state: Bool) -> Void) {
        Alamofire.request(.GET, url, parameters: params, encoding: .URL, headers: nil).responseJSON { (response) in
            switch response.result {
            case .Success(let value) :
                if value.isKindOfClass(NSDictionary) {
                    complete(result: value, state: true)
                }
            case .Failure(let error) :
                complete(result: error, state: false)
            }
        }
    }
