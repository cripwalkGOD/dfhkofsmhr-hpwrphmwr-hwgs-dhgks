function e(e, t) {
    const r = Object.create(null),
        a = e.split(",");
    for (let e = 0; e < a.length; e++) r[a[e]] = !0;
    return t ? e => !!r[e.toLowerCase()] : e => !!r[e]
}
const t = e("Infinity,undefined,NaN,isFinite,isNaN,parseFloat,parseInt,decodeURI,decodeURIComponent,encodeURI,encodeURIComponent,Math,Number,Date,Array,Object,Boolean,String,RegExp,Map,Set,JSON,Intl"),
    r = e("itemscope,allowfullscreen,formnovalidate,ismap,nomodule,novalidate,readonly");

function a(e) {
    if (k(e)) {
        const t = {};
        for (let r = 0; r < e.length; r++) {
            const n = e[r],
                o = a(x(n) ? i(n) : n);
            if (o)
                for (const e in o) t[e] = o[e]
        }
        return t
    }
    if (O(e)) return e
}
const n = /;(?![^(]*\))/g,
    o = /:(.+)/;

function i(e) {
    const t = {};
    return e.split(n).forEach((e => {
        if (e) {
            const r = e.split(o);
            r.length > 1 && (t[r[0].trim()] = r[1].trim())
        }
    })), t
}

function s(e) {
    let t = "";
    if (x(e)) t = e;
    else if (k(e))
        for (let r = 0; r < e.length; r++) t += s(e[r]) + " ";
    else if (O(e))
        for (const r in e) e[r] && (t += r + " ");
    return t.trim()
}

function l(e, t) {
    if (e === t) return !0;
    let r = C(e),
        a = C(t);
    if (r || a) return !(!r || !a) && e.getTime() === t.getTime();
    if (r = k(e), a = k(t), r || a) return !(!r || !a) && function(e, t) {
        if (e.length !== t.length) return !1;
        let r = !0;
        for (let a = 0; r && a < e.length; a++) r = l(e[a], t[a]);
        return r
    }(e, t);
    if (r = O(e), a = O(t), r || a) {
        if (!r || !a) return !1;
        if (Object.keys(e).length !== Object.keys(t).length) return !1;
        for (const r in e) {
            const a = e.hasOwnProperty(r),
                n = t.hasOwnProperty(r);
            if (a && !n || !a && n || !l(e[r], t[r])) return !1
        }
    }
    return String(e) === String(t)
}

function c(e, t) {
    return e.findIndex((e => l(e, t)))
}
const u = e => null == e ? "" : O(e) ? JSON.stringify(e, d, 2) : String(e),
    d = (e, t) => _(t) ? {
        [`Map(${t.size})`]: [...t.entries()].reduce(((e, [t, r]) => (e[`${t} =>`] = r, e)), {})
    } : S(t) ? {
        [`Set(${t.size})`]: [...t.values()]
    } : !O(t) || k(t) || A(t) ? t : String(t),
    h = {},
    p = [],
    f = () => {},
    m = () => !1,
    v = /^on[^a-z]/,
    g = e => v.test(e),
    y = e => e.startsWith("onUpdate:"),
    b = Object.assign,
    w = (e, t) => {
        const r = e.indexOf(t);
        r > -1 && e.splice(r, 1)
    },
    E = Object.prototype.hasOwnProperty,
    P = (e, t) => E.call(e, t),
    k = Array.isArray,
    _ = e => "[object Map]" === $(e),
    S = e => "[object Set]" === $(e),
    C = e => e instanceof Date,
    T = e => "function" == typeof e,
    x = e => "string" == typeof e,
    D = e => "symbol" == typeof e,
    O = e => null !== e && "object" == typeof e,
    R = e => O(e) && T(e.then) && T(e.catch),
    F = Object.prototype.toString,
    $ = e => F.call(e),
    A = e => "[object Object]" === $(e),
    M = e => x(e) && "NaN" !== e && "-" !== e[0] && "" + parseInt(e, 10) === e,
    L = e(",key,ref,onVnodeBeforeMount,onVnodeMounted,onVnodeBeforeUpdate,onVnodeUpdated,onVnodeBeforeUnmount,onVnodeUnmounted"),
    N = e => {
        const t = Object.create(null);
        return r => t[r] || (t[r] = e(r))
    },
    I = /-(\w)/g,
    j = N((e => e.replace(I, ((e, t) => t ? t.toUpperCase() : "")))),
    U = /\B([A-Z])/g,
    H = N((e => e.replace(U, "-$1").toLowerCase())),
    q = N((e => e.charAt(0).toUpperCase() + e.slice(1))),
    Y = N((e => e ? `on${q(e)}` : "")),
    B = (e, t) => e !== t && (e == e || t == t),
    W = (e, t) => {
        for (let r = 0; r < e.length; r++) e[r](t)
    },
    V = (e, t, r) => {
        Object.defineProperty(e, t, {
            configurable: !0,
            enumerable: !1,
            value: r
        })
    },
    z = e => {
        const t = parseFloat(e);
        return isNaN(t) ? e : t
    },
    X = new WeakMap,
    Q = [];
let G;
const K = Symbol(""),
    J = Symbol("");

function Z(e, t = h) {
    (function(e) {
        return e && !0 === e._isEffect
    })(e) && (e = e.raw);
    const r = function(e, t) {
        const r = function() {
            if (!r.active) return t.scheduler ? void 0 : e();
            if (!Q.includes(r)) {
                re(r);
                try {
                    return ne.push(ae), ae = !0, Q.push(r), G = r, e()
                } finally {
                    Q.pop(), ie(), G = Q[Q.length - 1]
                }
            }
        };
        return r.id = te++, r.allowRecurse = !!t.allowRecurse, r._isEffect = !0, r.active = !0, r.raw = e, r.deps = [], r.options = t, r
    }(e, t);
    return t.lazy || r(), r
}

function ee(e) {
    e.active && (re(e), e.options.onStop && e.options.onStop(), e.active = !1)
}
let te = 0;

function re(e) {
    const {
        deps: t
    } = e;
    if (t.length) {
        for (let r = 0; r < t.length; r++) t[r].delete(e);
        t.length = 0
    }
}
let ae = !0;
const ne = [];

function oe() {
    ne.push(ae), ae = !1
}

function ie() {
    const e = ne.pop();
    ae = void 0 === e || e
}

function se(e, t, r) {
    if (!ae || void 0 === G) return;
    let a = X.get(e);
    a || X.set(e, a = new Map);
    let n = a.get(r);
    n || a.set(r, n = new Set), n.has(G) || (n.add(G), G.deps.push(n))
}

function le(e, t, r, a, n, o) {
    const i = X.get(e);
    if (!i) return;
    const s = new Set,
        l = e => {
            e && e.forEach((e => {
                (e !== G || e.allowRecurse) && s.add(e)
            }))
        };
    if ("clear" === t) i.forEach(l);
    else if ("length" === r && k(e)) i.forEach(((e, t) => {
        ("length" === t || t >= a) && l(e)
    }));
    else switch (void 0 !== r && l(i.get(r)), t) {
        case "add":
            k(e) ? M(r) && l(i.get("length")) : (l(i.get(K)), _(e) && l(i.get(J)));
            break;
        case "delete":
            k(e) || (l(i.get(K)), _(e) && l(i.get(J)));
            break;
        case "set":
            _(e) && l(i.get(K))
    }
    s.forEach((e => {
        e.options.scheduler ? e.options.scheduler(e) : e()
    }))
}
const ce = new Set(Object.getOwnPropertyNames(Symbol).map((e => Symbol[e])).filter(D)),
    ue = me(),
    de = me(!1, !0),
    he = me(!0),
    pe = me(!0, !0),
    fe = {};

function me(e = !1, t = !1) {
    return function(r, a, n) {
        if ("__v_isReactive" === a) return !e;
        if ("__v_isReadonly" === a) return e;
        if ("__v_raw" === a && n === (e ? qe : He).get(r)) return r;
        const o = k(r);
        if (!e && o && P(fe, a)) return Reflect.get(fe, a, n);
        const i = Reflect.get(r, a, n);
        if (D(a) ? ce.has(a) : "__proto__" === a || "__v_isRef" === a) return i;
        if (e || se(r, 0, a), t) return i;
        if (Je(i)) {
            return !o || !M(a) ? i.value : i
        }
        return O(i) ? e ? We(i) : Be(i) : i
    }
} ["includes", "indexOf", "lastIndexOf"].forEach((e => {
    const t = Array.prototype[e];
    fe[e] = function(...e) {
        const r = Ge(this);
        for (let e = 0, t = this.length; e < t; e++) se(r, 0, e + "");
        const a = t.apply(r, e);
        return -1 === a || !1 === a ? t.apply(r, e.map(Ge)) : a
    }
})), ["push", "pop", "shift", "unshift", "splice"].forEach((e => {
    const t = Array.prototype[e];
    fe[e] = function(...e) {
        oe();
        const r = t.apply(this, e);
        return ie(), r
    }
}));

function ve(e = !1) {
    return function(t, r, a, n) {
        const o = t[r];
        if (!e && (a = Ge(a), !k(t) && Je(o) && !Je(a))) return o.value = a, !0;
        const i = k(t) && M(r) ? Number(r) < t.length : P(t, r),
            s = Reflect.set(t, r, a, n);
        return t === Ge(n) && (i ? B(a, o) && le(t, "set", r, a) : le(t, "add", r, a)), s
    }
}
const ge = {
        get: ue,
        set: ve(),
        deleteProperty: function(e, t) {
            const r = P(e, t),
                a = (e[t], Reflect.deleteProperty(e, t));
            return a && r && le(e, "delete", t, void 0), a
        },
        has: function(e, t) {
            const r = Reflect.has(e, t);
            return D(t) && ce.has(t) || se(e, 0, t), r
        },
        ownKeys: function(e) {
            return se(e, 0, k(e) ? "length" : K), Reflect.ownKeys(e)
        }
    },
    ye = {
        get: he,
        set: (e, t) => !0,
        deleteProperty: (e, t) => !0
    },
    be = b({}, ge, {
        get: de,
        set: ve(!0)
    }),
    we = (b({}, ye, {
        get: pe
    }), e => O(e) ? Be(e) : e),
    Ee = e => O(e) ? We(e) : e,
    Pe = e => e,
    ke = e => Reflect.getPrototypeOf(e);

function _e(e, t, r = !1, a = !1) {
    const n = Ge(e = e.__v_raw),
        o = Ge(t);
    t !== o && !r && se(n, 0, t), !r && se(n, 0, o);
    const {
        has: i
    } = ke(n), s = r ? Ee : a ? Pe : we;
    return i.call(n, t) ? s(e.get(t)) : i.call(n, o) ? s(e.get(o)) : void 0
}

function Se(e, t = !1) {
    const r = this.__v_raw,
        a = Ge(r),
        n = Ge(e);
    return e !== n && !t && se(a, 0, e), !t && se(a, 0, n), e === n ? r.has(e) : r.has(e) || r.has(n)
}

function Ce(e, t = !1) {
    return e = e.__v_raw, !t && se(Ge(e), 0, K), Reflect.get(e, "size", e)
}

function Te(e) {
    e = Ge(e);
    const t = Ge(this),
        r = ke(t).has.call(t, e);
    return t.add(e), r || le(t, "add", e, e), this
}

function xe(e, t) {
    t = Ge(t);
    const r = Ge(this),
        {
            has: a,
            get: n
        } = ke(r);
    let o = a.call(r, e);
    o || (e = Ge(e), o = a.call(r, e));
    const i = n.call(r, e);
    return r.set(e, t), o ? B(t, i) && le(r, "set", e, t) : le(r, "add", e, t), this
}

function De(e) {
    const t = Ge(this),
        {
            has: r,
            get: a
        } = ke(t);
    let n = r.call(t, e);
    n || (e = Ge(e), n = r.call(t, e));
    a && a.call(t, e);
    const o = t.delete(e);
    return n && le(t, "delete", e, void 0), o
}

function Oe() {
    const e = Ge(this),
        t = 0 !== e.size,
        r = e.clear();
    return t && le(e, "clear", void 0, void 0), r
}

function Re(e, t) {
    return function(r, a) {
        const n = this,
            o = n.__v_raw,
            i = Ge(o),
            s = e ? Ee : t ? Pe : we;
        return !e && se(i, 0, K), o.forEach(((e, t) => r.call(a, s(e), s(t), n)))
    }
}

function Fe(e, t, r) {
    return function(...a) {
        const n = this.__v_raw,
            o = Ge(n),
            i = _(o),
            s = "entries" === e || e === Symbol.iterator && i,
            l = "keys" === e && i,
            c = n[e](...a),
            u = t ? Ee : r ? Pe : we;
        return !t && se(o, 0, l ? J : K), {
            next() {
                const {
                    value: e,
                    done: t
                } = c.next();
                return t ? {
                    value: e,
                    done: t
                } : {
                    value: s ? [u(e[0]), u(e[1])] : u(e),
                    done: t
                }
            },
            [Symbol.iterator]() {
                return this
            }
        }
    }
}

function $e(e) {
    return function(...t) {
        return "delete" !== e && this
    }
}
const Ae = {
        get(e) {
            return _e(this, e)
        },
        get size() {
            return Ce(this)
        },
        has: Se,
        add: Te,
        set: xe,
        delete: De,
        clear: Oe,
        forEach: Re(!1, !1)
    },
    Me = {
        get(e) {
            return _e(this, e, !1, !0)
        },
        get size() {
            return Ce(this)
        },
        has: Se,
        add: Te,
        set: xe,
        delete: De,
        clear: Oe,
        forEach: Re(!1, !0)
    },
    Le = {
        get(e) {
            return _e(this, e, !0)
        },
        get size() {
            return Ce(this, !0)
        },
        has(e) {
            return Se.call(this, e, !0)
        },
        add: $e("add"),
        set: $e("set"),
        delete: $e("delete"),
        clear: $e("clear"),
        forEach: Re(!0, !1)
    };

function Ne(e, t) {
    const r = t ? Me : e ? Le : Ae;
    return (t, a, n) => "__v_isReactive" === a ? !e : "__v_isReadonly" === a ? e : "__v_raw" === a ? t : Reflect.get(P(r, a) && a in t ? r : t, a, n)
} ["keys", "values", "entries", Symbol.iterator].forEach((e => {
    Ae[e] = Fe(e, !1, !1), Le[e] = Fe(e, !0, !1), Me[e] = Fe(e, !1, !0)
}));
const Ie = {
        get: Ne(!1, !1)
    },
    je = {
        get: Ne(!1, !0)
    },
    Ue = {
        get: Ne(!0, !1)
    },
    He = new WeakMap,
    qe = new WeakMap;

function Ye(e) {
    return e.__v_skip || !Object.isExtensible(e) ? 0 : function(e) {
        switch (e) {
            case "Object":
            case "Array":
                return 1;
            case "Map":
            case "Set":
            case "WeakMap":
            case "WeakSet":
                return 2;
            default:
                return 0
        }
    }((e => $(e).slice(8, -1))(e))
}

function Be(e) {
    return e && e.__v_isReadonly ? e : Ve(e, !1, ge, Ie)
}

function We(e) {
    return Ve(e, !0, ye, Ue)
}

function Ve(e, t, r, a) {
    if (!O(e)) return e;
    if (e.__v_raw && (!t || !e.__v_isReactive)) return e;
    const n = t ? qe : He,
        o = n.get(e);
    if (o) return o;
    const i = Ye(e);
    if (0 === i) return e;
    const s = new Proxy(e, 2 === i ? a : r);
    return n.set(e, s), s
}

function ze(e) {
    return Xe(e) ? ze(e.__v_raw) : !(!e || !e.__v_isReactive)
}

function Xe(e) {
    return !(!e || !e.__v_isReadonly)
}

function Qe(e) {
    return ze(e) || Xe(e)
}

function Ge(e) {
    return e && Ge(e.__v_raw) || e
}
const Ke = e => O(e) ? Be(e) : e;

function Je(e) {
    return Boolean(e && !0 === e.__v_isRef)
}

function Ze(e) {
    return tt(e)
}
class et {
    constructor(e, t = !1) {
        this._rawValue = e, this._shallow = t, this.__v_isRef = !0, this._value = t ? e : Ke(e)
    }
    get value() {
        return se(Ge(this), 0, "value"), this._value
    }
    set value(e) {
        B(Ge(e), this._rawValue) && (this._rawValue = e, this._value = this._shallow ? e : Ke(e), le(Ge(this), "set", "value", e))
    }
}

function tt(e, t = !1) {
    return Je(e) ? e : new et(e, t)
}

function rt(e) {
    return Je(e) ? e.value : e
}
const at = {
    get: (e, t, r) => rt(Reflect.get(e, t, r)),
    set: (e, t, r, a) => {
        const n = e[t];
        return Je(n) && !Je(r) ? (n.value = r, !0) : Reflect.set(e, t, r, a)
    }
};

function nt(e) {
    return ze(e) ? e : new Proxy(e, at)
}
class ot {
    constructor(e, t) {
        this._object = e, this._key = t, this.__v_isRef = !0
    }
    get value() {
        return this._object[this._key]
    }
    set value(e) {
        this._object[this._key] = e
    }
}
class it {
    constructor(e, t, r) {
        this._setter = t, this._dirty = !0, this.__v_isRef = !0, this.effect = Z(e, {
            lazy: !0,
            scheduler: () => {
                this._dirty || (this._dirty = !0, le(Ge(this), "set", "value"))
            }
        }), this.__v_isReadonly = r
    }
    get value() {
        return this._dirty && (this._value = this.effect(), this._dirty = !1), se(Ge(this), 0, "value"), this._value
    }
    set value(e) {
        this._setter(e)
    }
}

function st(e, t, r, a) {
    let n;
    try {
        n = a ? e(...a) : e()
    } catch (e) {
        ct(e, t, r)
    }
    return n
}

function lt(e, t, r, a) {
    if (T(e)) {
        const n = st(e, t, r, a);
        return n && R(n) && n.catch((e => {
            ct(e, t, r)
        })), n
    }
    const n = [];
    for (let o = 0; o < e.length; o++) n.push(lt(e[o], t, r, a));
    return n
}

function ct(e, t, r, a = !0) {
    t && t.vnode;
    if (t) {
        let a = t.parent;
        const n = t.proxy,
            o = r;
        for (; a;) {
            const t = a.ec;
            if (t)
                for (let r = 0; r < t.length; r++)
                    if (!1 === t[r](e, n, o)) return;
            a = a.parent
        }
        const i = t.appContext.config.errorHandler;
        if (i) return void st(i, null, 10, [e, n, o])
    }! function(e, t, r, a = !0) {
        console.error(e)
    }(e, 0, 0, a)
}
let ut = !1,
    dt = !1;
const ht = [];
let pt = 0;
const ft = [];
let mt = null,
    vt = 0;
const gt = [];
let yt = null,
    bt = 0;
const wt = Promise.resolve();
let Et = null,
    Pt = null;

function kt(e) {
    const t = Et || wt;
    return e ? t.then(this ? e.bind(this) : e) : t
}

function _t(e) {
    ht.length && ht.includes(e, ut && e.allowRecurse ? pt + 1 : pt) || e === Pt || (ht.push(e), St())
}

function St() {
    ut || dt || (dt = !0, Et = wt.then(Ot))
}

function Ct(e, t, r, a) {
    k(e) ? r.push(...e) : t && t.includes(e, e.allowRecurse ? a + 1 : a) || r.push(e), St()
}

function Tt(e, t = null) {
    if (ft.length) {
        for (Pt = t, mt = [...new Set(ft)], ft.length = 0, vt = 0; vt < mt.length; vt++) mt[vt]();
        mt = null, vt = 0, Pt = null, Tt(e, t)
    }
}

function xt(e) {
    if (gt.length) {
        const e = [...new Set(gt)];
        if (gt.length = 0, yt) return void yt.push(...e);
        for (yt = e, yt.sort(((e, t) => Dt(e) - Dt(t))), bt = 0; bt < yt.length; bt++) yt[bt]();
        yt = null, bt = 0
    }
}
const Dt = e => null == e.id ? 1 / 0 : e.id;

function Ot(e) {
    dt = !1, ut = !0, Tt(e), ht.sort(((e, t) => Dt(e) - Dt(t)));
    try {
        for (pt = 0; pt < ht.length; pt++) {
            const e = ht[pt];
            e && st(e, null, 14)
        }
    } finally {
        pt = 0, ht.length = 0, xt(), ut = !1, Et = null, (ht.length || gt.length) && Ot(e)
    }
}

function Rt(e, t, ...r) {
    const a = e.vnode.props || h;
    let n = r;
    const o = t.startsWith("update:"),
        i = o && t.slice(7);
    if (i && i in a) {
        const e = `${"modelValue"===i?"model":i}Modifiers`,
            {
                number: t,
                trim: o
            } = a[e] || h;
        o ? n = r.map((e => e.trim())) : t && (n = r.map(z))
    }
    let s = Y(j(t)),
        l = a[s];
    !l && o && (s = Y(H(t)), l = a[s]), l && lt(l, e, 6, n);
    const c = a[s + "Once"];
    if (c) {
        if (e.emitted) {
            if (e.emitted[s]) return
        } else(e.emitted = {})[s] = !0;
        lt(c, e, 6, n)
    }
}

function Ft(e, t, r = !1) {
    if (!t.deopt && void 0 !== e.__emits) return e.__emits;
    const a = e.emits;
    let n = {},
        o = !1;
    if (!T(e)) {
        const a = e => {
            o = !0, b(n, Ft(e, t, !0))
        };
        !r && t.mixins.length && t.mixins.forEach(a), e.extends && a(e.extends), e.mixins && e.mixins.forEach(a)
    }
    return a || o ? (k(a) ? a.forEach((e => n[e] = null)) : b(n, a), e.__emits = n) : e.__emits = null
}

function $t(e, t) {
    return !(!e || !g(t)) && (t = t.slice(2).replace(/Once$/, ""), P(e, t[0].toLowerCase() + t.slice(1)) || P(e, H(t)) || P(e, t))
}
let At = null;

function Mt(e) {
    At = e
}

function Lt(e) {
    const {
        type: t,
        vnode: r,
        proxy: a,
        withProxy: n,
        props: o,
        propsOptions: [i],
        slots: s,
        attrs: l,
        emit: c,
        render: u,
        renderCache: d,
        data: h,
        setupState: p,
        ctx: f
    } = e;
    let m;
    At = e;
    try {
        let e;
        if (4 & r.shapeFlag) {
            const t = n || a;
            m = Sa(u.call(t, t, d, o, p, h, f)), e = l
        } else {
            const r = t;
            0, m = Sa(r.length > 1 ? r(o, {
                attrs: l,
                slots: s,
                emit: c
            }) : r(o, null)), e = t.props ? l : It(l)
        }
        let v = m;
        if (!1 !== t.inheritAttrs && e) {
            const t = Object.keys(e),
                {
                    shapeFlag: r
                } = v;
            t.length && (1 & r || 6 & r) && (i && t.some(y) && (e = jt(e, i)), v = Ea(v, e))
        }
        r.dirs && (v.dirs = v.dirs ? v.dirs.concat(r.dirs) : r.dirs), r.transition && (v.transition = r.transition), m = v
    } catch (t) {
        ct(t, e, 1), m = wa(la)
    }
    return At = null, m
}

function Nt(e) {
    let t;
    for (let r = 0; r < e.length; r++) {
        const a = e[r];
        if (!ma(a)) return;
        if (a.type !== la || "v-if" === a.children) {
            if (t) return;
            t = a
        }
    }
    return t
}
const It = e => {
        let t;
        for (const r in e)("class" === r || "style" === r || g(r)) && ((t || (t = {}))[r] = e[r]);
        return t
    },
    jt = (e, t) => {
        const r = {};
        for (const a in e) y(a) && a.slice(9) in t || (r[a] = e[a]);
        return r
    };

function Ut(e, t, r) {
    const a = Object.keys(t);
    if (a.length !== Object.keys(e).length) return !0;
    for (let n = 0; n < a.length; n++) {
        const o = a[n];
        if (t[o] !== e[o] && !$t(r, o)) return !0
    }
    return !1
}

function Ht(e) {
    if (T(e) && (e = e()), k(e)) {
        e = Nt(e)
    }
    return Sa(e)
}
let qt = 0;
const Yt = e => qt += e;

function Bt(e, t, r = {}, a) {
    let n = e[t];
    qt++, ha();
    const o = n && Wt(n(r)),
        i = fa(ia, {
            key: r.key || `_${t}`
        }, o || (a ? a() : []), o && 1 === e._ ? 64 : -2);
    return qt--, i
}

function Wt(e) {
    return e.some((e => !ma(e) || e.type !== la && !(e.type === ia && !Wt(e.children)))) ? e : null
}

function Vt(e, t = At) {
    if (!t) return e;
    const r = (...r) => {
        qt || ha(!0);
        const a = At;
        Mt(t);
        const n = e(...r);
        return Mt(a), qt || pa(), n
    };
    return r._c = !0, r
}
let zt = null;
const Xt = [];

function Qt(e) {
    Xt.push(zt = e)
}

function Gt() {
    Xt.pop(), zt = Xt[Xt.length - 1] || null
}

function Kt(e) {
    return t => Vt((function() {
        Qt(e);
        const r = t.apply(this, arguments);
        return Gt(), r
    }))
}

function Jt(e, t, r, a = !1) {
    const n = {},
        o = {};
    V(o, ga, 1), Zt(e, t, n, o), r ? e.props = a ? n : Ve(n, !1, be, je) : e.type.props ? e.props = n : e.props = o, e.attrs = o
}

function Zt(e, t, r, a) {
    const [n, o] = e.propsOptions;
    if (t)
        for (const o in t) {
            const i = t[o];
            if (L(o)) continue;
            let s;
            n && P(n, s = j(o)) ? r[s] = i : $t(e.emitsOptions, o) || (a[o] = i)
        }
    if (o) {
        const t = Ge(r);
        for (let a = 0; a < o.length; a++) {
            const i = o[a];
            r[i] = er(n, t, i, t[i], e)
        }
    }
}

function er(e, t, r, a, n) {
    const o = e[r];
    if (null != o) {
        const e = P(o, "default");
        if (e && void 0 === a) {
            const e = o.default;
            o.type !== Function && T(e) ? (za(n), a = e(t), za(null)) : a = e
        }
        o[0] && (P(t, r) || e ? !o[1] || "" !== a && a !== H(r) || (a = !0) : a = !1)
    }
    return a
}

function tr(e, t, r = !1) {
    if (!t.deopt && e.__props) return e.__props;
    const a = e.props,
        n = {},
        o = [];
    let i = !1;
    if (!T(e)) {
        const a = e => {
            i = !0;
            const [r, a] = tr(e, t, !0);
            b(n, r), a && o.push(...a)
        };
        !r && t.mixins.length && t.mixins.forEach(a), e.extends && a(e.extends), e.mixins && e.mixins.forEach(a)
    }
    if (!a && !i) return e.__props = p;
    if (k(a))
        for (let e = 0; e < a.length; e++) {
            const t = j(a[e]);
            rr(t) && (n[t] = h)
        } else if (a)
            for (const e in a) {
                const t = j(e);
                if (rr(t)) {
                    const r = a[e],
                        i = n[t] = k(r) || T(r) ? {
                            type: r
                        } : r;
                    if (i) {
                        const e = or(Boolean, i.type),
                            r = or(String, i.type);
                        i[0] = e > -1, i[1] = r < 0 || e < r, (e > -1 || P(i, "default")) && o.push(t)
                    }
                }
            }
    return e.__props = [n, o]
}

function rr(e) {
    return "$" !== e[0]
}

function ar(e) {
    const t = e && e.toString().match(/^\s*function (\w+)/);
    return t ? t[1] : ""
}

function nr(e, t) {
    return ar(e) === ar(t)
}

function or(e, t) {
    if (k(t)) {
        for (let r = 0, a = t.length; r < a; r++)
            if (nr(t[r], e)) return r
    } else if (T(t)) return nr(t, e) ? 0 : -1;
    return -1
}

function ir(e, t, r = Wa, a = !1) {
    if (r) {
        const n = r[e] || (r[e] = []),
            o = t.__weh || (t.__weh = (...a) => {
                if (r.isUnmounted) return;
                oe(), za(r);
                const n = lt(t, r, e, a);
                return za(null), ie(), n
            });
        return a ? n.unshift(o) : n.push(o), o
    }
}
const sr = e => (t, r = Wa) => !Xa && ir(e, t, r),
    lr = sr("bm"),
    cr = sr("m"),
    ur = sr("bu"),
    dr = sr("u"),
    hr = sr("bum"),
    pr = sr("um"),
    fr = sr("rtg"),
    mr = sr("rtc");

function vr(e, t) {
    return br(e, null, t)
}
const gr = {};

function yr(e, t, r) {
    return br(e, t, r)
}

function br(e, t, {
    immediate: r,
    deep: a,
    flush: n,
    onTrack: o,
    onTrigger: i
} = h, s = Wa) {
    let l, c, u = !1;
    if (Je(e) ? (l = () => e.value, u = !!e._shallow) : ze(e) ? (l = () => e, a = !0) : l = k(e) ? () => e.map((e => Je(e) ? e.value : ze(e) ? Er(e) : T(e) ? st(e, s, 2) : void 0)) : T(e) ? t ? () => st(e, s, 2) : () => {
            if (!s || !s.isUnmounted) return c && c(), st(e, s, 3, [d])
        } : f, t && a) {
        const e = l;
        l = () => Er(e())
    }
    const d = e => {
        c = g.options.onStop = () => {
            st(e, s, 4)
        }
    };
    let p = k(e) ? [] : gr;
    const m = () => {
        if (g.active)
            if (t) {
                const e = g();
                (a || u || B(e, p)) && (c && c(), lt(t, s, 3, [e, p === gr ? void 0 : p, d]), p = e)
            } else g()
    };
    let v;
    m.allowRecurse = !!t, v = "sync" === n ? m : "post" === n ? () => Wr(m, s && s.suspense) : () => {
        !s || s.isMounted ? function(e) {
            Ct(e, mt, ft, vt)
        }(m) : m()
    };
    const g = Z(l, {
        lazy: !0,
        onTrack: o,
        onTrigger: i,
        scheduler: v
    });
    return Ka(g, s), t ? r ? m() : p = g() : "post" === n ? Wr(g, s && s.suspense) : g(), () => {
        ee(g), s && w(s.effects, g)
    }
}

function wr(e, t, r) {
    const a = this.proxy;
    return br(x(e) ? () => a[e] : e.bind(a), t.bind(a), r, this)
}

function Er(e, t = new Set) {
    if (!O(e) || t.has(e)) return e;
    if (t.add(e), Je(e)) Er(e.value, t);
    else if (k(e))
        for (let r = 0; r < e.length; r++) Er(e[r], t);
    else if (S(e) || _(e)) e.forEach((e => {
        Er(e, t)
    }));
    else
        for (const r in e) Er(e[r], t);
    return e
}
const Pr = [Function, Array],
    kr = {
        name: "BaseTransition",
        props: {
            mode: String,
            appear: Boolean,
            persisted: Boolean,
            onBeforeEnter: Pr,
            onEnter: Pr,
            onAfterEnter: Pr,
            onEnterCancelled: Pr,
            onBeforeLeave: Pr,
            onLeave: Pr,
            onAfterLeave: Pr,
            onLeaveCancelled: Pr,
            onBeforeAppear: Pr,
            onAppear: Pr,
            onAfterAppear: Pr,
            onAppearCancelled: Pr
        },
        setup(e, {
            slots: t
        }) {
            const r = Va(),
                a = function() {
                    const e = {
                        isMounted: !1,
                        isLeaving: !1,
                        isUnmounting: !1,
                        leavingVNodes: new Map
                    };
                    return cr((() => {
                        e.isMounted = !0
                    })), hr((() => {
                        e.isUnmounting = !0
                    })), e
                }();
            let n;
            return () => {
                const o = t.default && Dr(t.default(), !0);
                if (!o || !o.length) return;
                const i = Ge(e),
                    {
                        mode: s
                    } = i,
                    l = o[0];
                if (a.isLeaving) return Cr(l);
                const c = Tr(l);
                if (!c) return Cr(l);
                const u = Sr(c, i, a, r);
                xr(c, u);
                const d = r.subTree,
                    h = d && Tr(d);
                let p = !1;
                const {
                    getTransitionKey: f
                } = c.type;
                if (f) {
                    const e = f();
                    void 0 === n ? n = e : e !== n && (n = e, p = !0)
                }
                if (h && h.type !== la && (!va(c, h) || p)) {
                    const e = Sr(h, i, a, r);
                    if (xr(h, e), "out-in" === s) return a.isLeaving = !0, e.afterLeave = () => {
                        a.isLeaving = !1, r.update()
                    }, Cr(l);
                    "in-out" === s && (e.delayLeave = (e, t, r) => {
                        _r(a, h)[String(h.key)] = h, e._leaveCb = () => {
                            t(), e._leaveCb = void 0, delete u.delayedLeave
                        }, u.delayedLeave = r
                    })
                }
                return l
            }
        }
    };

function _r(e, t) {
    const {
        leavingVNodes: r
    } = e;
    let a = r.get(t.type);
    return a || (a = Object.create(null), r.set(t.type, a)), a
}

function Sr(e, t, r, a) {
    const {
        appear: n,
        mode: o,
        persisted: i = !1,
        onBeforeEnter: s,
        onEnter: l,
        onAfterEnter: c,
        onEnterCancelled: u,
        onBeforeLeave: d,
        onLeave: h,
        onAfterLeave: p,
        onLeaveCancelled: f,
        onBeforeAppear: m,
        onAppear: v,
        onAfterAppear: g,
        onAppearCancelled: y
    } = t, b = String(e.key), w = _r(r, e), E = (e, t) => {
        e && lt(e, a, 9, t)
    }, P = {
        mode: o,
        persisted: i,
        beforeEnter(t) {
            let a = s;
            if (!r.isMounted) {
                if (!n) return;
                a = m || s
            }
            t._leaveCb && t._leaveCb(!0);
            const o = w[b];
            o && va(e, o) && o.el._leaveCb && o.el._leaveCb(), E(a, [t])
        },
        enter(e) {
            let t = l,
                a = c,
                o = u;
            if (!r.isMounted) {
                if (!n) return;
                t = v || l, a = g || c, o = y || u
            }
            let i = !1;
            const s = e._enterCb = t => {
                i || (i = !0, E(t ? o : a, [e]), P.delayedLeave && P.delayedLeave(), e._enterCb = void 0)
            };
            t ? (t(e, s), t.length <= 1 && s()) : s()
        },
        leave(t, a) {
            const n = String(e.key);
            if (t._enterCb && t._enterCb(!0), r.isUnmounting) return a();
            E(d, [t]);
            let o = !1;
            const i = t._leaveCb = r => {
                o || (o = !0, a(), E(r ? f : p, [t]), t._leaveCb = void 0, w[n] === e && delete w[n])
            };
            w[n] = e, h ? (h(t, i), h.length <= 1 && i()) : i()
        },
        clone: e => Sr(e, t, r, a)
    };
    return P
}

function Cr(e) {
    if (Or(e)) return (e = Ea(e)).children = null, e
}

function Tr(e) {
    return Or(e) ? e.children ? e.children[0] : void 0 : e
}

function xr(e, t) {
    6 & e.shapeFlag && e.component ? xr(e.component.subTree, t) : 128 & e.shapeFlag ? (e.ssContent.transition = t.clone(e.ssContent), e.ssFallback.transition = t.clone(e.ssFallback)) : e.transition = t
}

function Dr(e, t = !1) {
    let r = [],
        a = 0;
    for (let n = 0; n < e.length; n++) {
        const o = e[n];
        o.type === ia ? (128 & o.patchFlag && a++, r = r.concat(Dr(o.children, t))) : (t || o.type !== la) && r.push(o)
    }
    if (a > 1)
        for (let e = 0; e < r.length; e++) r[e].patchFlag = -2;
    return r
}
const Or = e => e.type.__isKeepAlive;

function Rr(e, t, r = Wa) {
    const a = e.__wdc || (e.__wdc = () => {
        let t = r;
        for (; t;) {
            if (t.isDeactivated) return;
            t = t.parent
        }
        e()
    });
    if (ir(t, a, r), r) {
        let e = r.parent;
        for (; e && e.parent;) Or(e.parent.vnode) && Fr(a, t, r, e), e = e.parent
    }
}

function Fr(e, t, r, a) {
    const n = ir(t, e, a, !0);
    pr((() => {
        w(a[t], n)
    }), r)
}
const $r = e => "_" === e[0] || "$stable" === e,
    Ar = e => k(e) ? e.map(Sa) : [Sa(e)],
    Mr = (e, t, r) => Vt((e => Ar(t(e))), r),
    Lr = (e, t) => {
        const r = e._ctx;
        for (const a in e) {
            if ($r(a)) continue;
            const n = e[a];
            if (T(n)) t[a] = Mr(0, n, r);
            else if (null != n) {
                const e = Ar(n);
                t[a] = () => e
            }
        }
    },
    Nr = (e, t) => {
        const r = Ar(t);
        e.slots.default = () => r
    };

function Ir(e, t) {
    if (null === At) return e;
    const r = At.proxy,
        a = e.dirs || (e.dirs = []);
    for (let e = 0; e < t.length; e++) {
        let [n, o, i, s = h] = t[e];
        T(n) && (n = {
            mounted: n,
            updated: n
        }), a.push({
            dir: n,
            instance: r,
            value: o,
            oldValue: void 0,
            arg: i,
            modifiers: s
        })
    }
    return e
}

function jr(e, t, r, a) {
    const n = e.dirs,
        o = t && t.dirs;
    for (let i = 0; i < n.length; i++) {
        const s = n[i];
        o && (s.oldValue = o[i].value);
        const l = s.dir[a];
        l && lt(l, r, 8, [e.el, s, e, t])
    }
}

function Ur() {
    return {
        app: null,
        config: {
            isNativeTag: m,
            performance: !1,
            globalProperties: {},
            optionMergeStrategies: {},
            isCustomElement: m,
            errorHandler: void 0,
            warnHandler: void 0
        },
        mixins: [],
        components: {},
        directives: {},
        provides: Object.create(null)
    }
}
let Hr = 0;

function qr(e, t) {
    return function(r, a = null) {
        null == a || O(a) || (a = null);
        const n = Ur(),
            o = new Set;
        let i = !1;
        const s = n.app = {
            _uid: Hr++,
            _component: r,
            _props: a,
            _container: null,
            _context: n,
            version: tn,
            get config() {
                return n.config
            },
            set config(e) {},
            use: (e, ...t) => (o.has(e) || (e && T(e.install) ? (o.add(e), e.install(s, ...t)) : T(e) && (o.add(e), e(s, ...t))), s),
            mixin: e => (n.mixins.includes(e) || (n.mixins.push(e), (e.props || e.emits) && (n.deopt = !0)), s),
            component: (e, t) => t ? (n.components[e] = t, s) : n.components[e],
            directive: (e, t) => t ? (n.directives[e] = t, s) : n.directives[e],
            mount(o, l) {
                if (!i) {
                    const c = wa(r, a);
                    return c.appContext = n, l && t ? t(c, o) : e(c, o), i = !0, s._container = o, o.__vue_app__ = s, c.component.proxy
                }
            },
            unmount() {
                i && e(null, s._container)
            },
            provide: (e, t) => (n.provides[e] = t, s)
        };
        return s
    }
}

function Yr(e) {
    return T(e) ? {
        setup: e,
        name: e.name
    } : e
}
const Br = {
        scheduler: _t,
        allowRecurse: !0
    },
    Wr = function(e, t) {
        t && t.pendingBranch ? k(e) ? t.effects.push(...e) : t.effects.push(e) : Ct(e, yt, gt, bt)
    },
    Vr = (e, t, r, a) => {
        if (k(e)) return void e.forEach(((e, n) => Vr(e, t && (k(t) ? t[n] : t), r, a)));
        let n;
        n = !a || a.type.__asyncLoader ? null : 4 & a.shapeFlag ? a.component.exposed || a.component.proxy : a.el;
        const {
            i: o,
            r: i
        } = e, s = t && t.r, l = o.refs === h ? o.refs = {} : o.refs, c = o.setupState;
        if (null != s && s !== i && (x(s) ? (l[s] = null, P(c, s) && (c[s] = null)) : Je(s) && (s.value = null)), x(i)) {
            const e = () => {
                l[i] = n, P(c, i) && (c[i] = n)
            };
            n ? (e.id = -1, Wr(e, r)) : e()
        } else if (Je(i)) {
            const e = () => {
                i.value = n
            };
            n ? (e.id = -1, Wr(e, r)) : e()
        } else T(i) && st(i, o, 12, [n, l])
    };

function zr(e) {
    return function(e, t) {
        const {
            insert: r,
            remove: a,
            patchProp: n,
            forcePatchProp: o,
            createElement: i,
            createText: s,
            createComment: l,
            setText: c,
            setElementText: u,
            parentNode: d,
            nextSibling: m,
            setScopeId: v = f,
            cloneNode: g,
            insertStaticContent: y
        } = e, w = (e, t, r, a = null, n = null, o = null, i = !1, s = !1) => {
            e && !va(e, t) && (a = ae(e), G(e, n, o, !0), e = null), -2 === t.patchFlag && (s = !1, t.dynamicChildren = null);
            const {
                type: l,
                ref: c,
                shapeFlag: u
            } = t;
            switch (l) {
                case sa:
                    E(e, t, r, a);
                    break;
                case la:
                    k(e, t, r, a);
                    break;
                case ca:
                    null == e && _(t, r, a, i);
                    break;
                case ia:
                    M(e, t, r, a, n, o, i, s);
                    break;
                default:
                    1 & u ? T(e, t, r, a, n, o, i, s) : 6 & u ? N(e, t, r, a, n, o, i, s) : (64 & u || 128 & u) && l.process(e, t, r, a, n, o, i, s, se)
            }
            null != c && n && Vr(c, e && e.ref, o, t)
        }, E = (e, t, a, n) => {
            if (null == e) r(t.el = s(t.children), a, n);
            else {
                const r = t.el = e.el;
                t.children !== e.children && c(r, t.children)
            }
        }, k = (e, t, a, n) => {
            null == e ? r(t.el = l(t.children || ""), a, n) : t.el = e.el
        }, _ = (e, t, r, a) => {
            [e.el, e.anchor] = y(e.children, t, r, a)
        }, S = ({
            el: e,
            anchor: t
        }, a, n) => {
            let o;
            for (; e && e !== t;) o = m(e), r(e, a, n), e = o;
            r(t, a, n)
        }, C = ({
            el: e,
            anchor: t
        }) => {
            let r;
            for (; e && e !== t;) r = m(e), a(e), e = r;
            a(t)
        }, T = (e, t, r, a, n, o, i, s) => {
            i = i || "svg" === t.type, null == e ? x(t, r, a, n, o, i, s) : F(e, t, n, o, i, s)
        }, x = (e, t, a, o, s, l, c) => {
            let d, h;
            const {
                type: p,
                props: f,
                shapeFlag: m,
                transition: v,
                scopeId: y,
                patchFlag: b,
                dirs: w
            } = e;
            if (e.el && void 0 !== g && -1 === b) d = e.el = g(e.el);
            else {
                if (d = e.el = i(e.type, l, f && f.is), 8 & m ? u(d, e.children) : 16 & m && O(e.children, d, null, o, s, l && "foreignObject" !== p, c || !!e.dynamicChildren), w && jr(e, null, o, "created"), f) {
                    for (const t in f) L(t) || n(d, t, null, f[t], l, e.children, o, s, re);
                    (h = f.onVnodeBeforeMount) && Xr(h, o, e)
                }
                D(d, y, e, o)
            }
            w && jr(e, null, o, "beforeMount");
            const E = (!s || s && !s.pendingBranch) && v && !v.persisted;
            E && v.beforeEnter(d), r(d, t, a), ((h = f && f.onVnodeMounted) || E || w) && Wr((() => {
                h && Xr(h, o, e), E && v.enter(d), w && jr(e, null, o, "mounted")
            }), s)
        }, D = (e, t, r, a) => {
            if (t && v(e, t), a) {
                const n = a.type.__scopeId;
                n && n !== t && v(e, n + "-s"), r === a.subTree && D(e, a.vnode.scopeId, a.vnode, a.parent)
            }
        }, O = (e, t, r, a, n, o, i, s = 0) => {
            for (let l = s; l < e.length; l++) {
                const s = e[l] = i ? Ca(e[l]) : Sa(e[l]);
                w(null, s, t, r, a, n, o, i)
            }
        }, F = (e, t, r, a, i, s) => {
            const l = t.el = e.el;
            let {
                patchFlag: c,
                dynamicChildren: d,
                dirs: p
            } = t;
            c |= 16 & e.patchFlag;
            const f = e.props || h,
                m = t.props || h;
            let v;
            if ((v = m.onVnodeBeforeUpdate) && Xr(v, r, t, e), p && jr(t, e, r, "beforeUpdate"), c > 0) {
                if (16 & c) A(l, t, f, m, r, a, i);
                else if (2 & c && f.class !== m.class && n(l, "class", null, m.class, i), 4 & c && n(l, "style", f.style, m.style, i), 8 & c) {
                    const s = t.dynamicProps;
                    for (let t = 0; t < s.length; t++) {
                        const c = s[t],
                            u = f[c],
                            d = m[c];
                        (d !== u || o && o(l, c)) && n(l, c, u, d, i, e.children, r, a, re)
                    }
                }
                1 & c && e.children !== t.children && u(l, t.children)
            } else s || null != d || A(l, t, f, m, r, a, i);
            const g = i && "foreignObject" !== t.type;
            d ? $(e.dynamicChildren, d, l, r, a, g) : s || B(e, t, l, null, r, a, g), ((v = m.onVnodeUpdated) || p) && Wr((() => {
                v && Xr(v, r, t, e), p && jr(t, e, r, "updated")
            }), a)
        }, $ = (e, t, r, a, n, o) => {
            for (let i = 0; i < t.length; i++) {
                const s = e[i],
                    l = t[i],
                    c = s.type === ia || !va(s, l) || 6 & s.shapeFlag || 64 & s.shapeFlag ? d(s.el) : r;
                w(s, l, c, null, a, n, o, !0)
            }
        }, A = (e, t, r, a, i, s, l) => {
            if (r !== a) {
                for (const c in a) {
                    if (L(c)) continue;
                    const u = a[c],
                        d = r[c];
                    (u !== d || o && o(e, c)) && n(e, c, d, u, l, t.children, i, s, re)
                }
                if (r !== h)
                    for (const o in r) L(o) || o in a || n(e, o, r[o], null, l, t.children, i, s, re)
            }
        }, M = (e, t, a, n, o, i, l, c) => {
            const u = t.el = e ? e.el : s(""),
                d = t.anchor = e ? e.anchor : s("");
            let {
                patchFlag: h,
                dynamicChildren: p
            } = t;
            h > 0 && (c = !0), null == e ? (r(u, a, n), r(d, a, n), O(t.children, a, d, o, i, l, c)) : h > 0 && 64 & h && p ? ($(e.dynamicChildren, p, a, o, i, l), (null != t.key || o && t === o.subTree) && Qr(e, t, !0)) : B(e, t, a, d, o, i, l, c)
        }, N = (e, t, r, a, n, o, i, s) => {
            null == e ? 512 & t.shapeFlag ? n.ctx.activate(t, r, a, i, s) : I(t, r, a, n, o, i, s) : U(e, t, s)
        }, I = (e, t, r, a, n, o, i) => {
            const s = e.component = function(e, t, r) {
                const a = e.type,
                    n = (t ? t.appContext : e.appContext) || Ya,
                    o = {
                        uid: Ba++,
                        vnode: e,
                        type: a,
                        parent: t,
                        appContext: n,
                        root: null,
                        next: null,
                        subTree: null,
                        update: null,
                        render: null,
                        proxy: null,
                        exposed: null,
                        withProxy: null,
                        effects: null,
                        provides: t ? t.provides : Object.create(n.provides),
                        accessCache: null,
                        renderCache: [],
                        components: null,
                        directives: null,
                        propsOptions: tr(a, n),
                        emitsOptions: Ft(a, n),
                        emit: null,
                        emitted: null,
                        ctx: h,
                        data: h,
                        props: h,
                        attrs: h,
                        slots: h,
                        refs: h,
                        setupState: h,
                        setupContext: null,
                        suspense: r,
                        suspenseId: r ? r.pendingId : 0,
                        asyncDep: null,
                        asyncResolved: !1,
                        isMounted: !1,
                        isUnmounted: !1,
                        isDeactivated: !1,
                        bc: null,
                        c: null,
                        bm: null,
                        m: null,
                        bu: null,
                        u: null,
                        um: null,
                        bum: null,
                        da: null,
                        a: null,
                        rtg: null,
                        rtc: null,
                        ec: null
                    };
                return o.ctx = {
                    _: o
                }, o.root = t ? t.root : o, o.emit = Rt.bind(null, o), o
            }(e, a, n);
            if (Or(e) && (s.ctx.renderer = se), function(e, t = !1) {
                    Xa = t;
                    const {
                        props: r,
                        children: a,
                        shapeFlag: n
                    } = e.vnode, o = 4 & n;
                    Jt(e, r, o, t), ((e, t) => {
                        if (32 & e.vnode.shapeFlag) {
                            const r = t._;
                            r ? (e.slots = t, V(t, "_", r)) : Lr(t, e.slots = {})
                        } else e.slots = {}, t && Nr(e, t);
                        V(e.slots, ga, 1)
                    })(e, a);
                    const i = o ? function(e, t) {
                        const r = e.type;
                        e.accessCache = Object.create(null), e.proxy = new Proxy(e.ctx, Ha);
                        const {
                            setup: a
                        } = r;
                        if (a) {
                            const r = e.setupContext = a.length > 1 ? function(e) {
                                const t = t => {
                                    e.exposed = nt(t)
                                };
                                return {
                                    attrs: e.attrs,
                                    slots: e.slots,
                                    emit: e.emit,
                                    expose: t
                                }
                            }(e) : null;
                            Wa = e, oe();
                            const n = st(a, e, 0, [e.props, r]);
                            if (ie(), Wa = null, R(n)) {
                                if (t) return n.then((t => {
                                    Qa(e, t)
                                }));
                                e.asyncDep = n
                            } else Qa(e, n)
                        } else Ga(e)
                    }(e, t) : void 0;
                    Xa = !1
                }(s), s.asyncDep) {
                if (n && n.registerDep(s, q), !e.el) {
                    const e = s.subTree = wa(la);
                    k(null, e, t, r)
                }
            } else q(s, e, t, r, n, o, i)
        }, U = (e, t, r) => {
            const a = t.component = e.component;
            if (function(e, t, r) {
                    const {
                        props: a,
                        children: n,
                        component: o
                    } = e, {
                        props: i,
                        children: s,
                        patchFlag: l
                    } = t, c = o.emitsOptions;
                    if (t.dirs || t.transition) return !0;
                    if (!(r && l >= 0)) return !(!n && !s || s && s.$stable) || a !== i && (a ? !i || Ut(a, i, c) : !!i);
                    if (1024 & l) return !0;
                    if (16 & l) return a ? Ut(a, i, c) : !!i;
                    if (8 & l) {
                        const e = t.dynamicProps;
                        for (let t = 0; t < e.length; t++) {
                            const r = e[t];
                            if (i[r] !== a[r] && !$t(c, r)) return !0
                        }
                    }
                    return !1
                }(e, t, r)) {
                if (a.asyncDep && !a.asyncResolved) return void Y(a, t, r);
                a.next = t,
                    function(e) {
                        const t = ht.indexOf(e);
                        t > -1 && ht.splice(t, 1)
                    }(a.update), a.update()
            } else t.component = e.component, t.el = e.el, a.vnode = t
        }, q = (e, t, r, a, n, o, i) => {
            e.update = Z((function() {
                if (e.isMounted) {
                    let t, {
                            next: r,
                            bu: a,
                            u: s,
                            parent: l,
                            vnode: c
                        } = e,
                        u = r;
                    r ? (r.el = c.el, Y(e, r, i)) : r = c, a && W(a), (t = r.props && r.props.onVnodeBeforeUpdate) && Xr(t, l, r, c);
                    const h = Lt(e),
                        p = e.subTree;
                    e.subTree = h, w(p, h, d(p.el), ae(p), e, n, o), r.el = h.el, null === u && function({
                        vnode: e,
                        parent: t
                    }, r) {
                        for (; t && t.subTree === e;)(e = t.vnode).el = r, t = t.parent
                    }(e, h.el), s && Wr(s, n), (t = r.props && r.props.onVnodeUpdated) && Wr((() => {
                        Xr(t, l, r, c)
                    }), n)
                } else {
                    let i;
                    const {
                        el: s,
                        props: l
                    } = t, {
                        bm: c,
                        m: u,
                        parent: d
                    } = e;
                    c && W(c), (i = l && l.onVnodeBeforeMount) && Xr(i, d, t);
                    const h = e.subTree = Lt(e);
                    s && ue ? ue(t.el, h, e, n) : (w(null, h, r, a, e, n, o), t.el = h.el), u && Wr(u, n), (i = l && l.onVnodeMounted) && Wr((() => {
                        Xr(i, d, t)
                    }), n);
                    const {
                        a: p
                    } = e;
                    p && 256 & t.shapeFlag && Wr(p, n), e.isMounted = !0
                }
            }), Br)
        }, Y = (e, t, r) => {
            t.component = e;
            const a = e.vnode.props;
            e.vnode = t, e.next = null,
                function(e, t, r, a) {
                    const {
                        props: n,
                        attrs: o,
                        vnode: {
                            patchFlag: i
                        }
                    } = e, s = Ge(n), [l] = e.propsOptions;
                    if (!(a || i > 0) || 16 & i) {
                        let a;
                        Zt(e, t, n, o);
                        for (const o in s) t && (P(t, o) || (a = H(o)) !== o && P(t, a)) || (l ? !r || void 0 === r[o] && void 0 === r[a] || (n[o] = er(l, t || h, o, void 0, e)) : delete n[o]);
                        if (o !== s)
                            for (const e in o) t && P(t, e) || delete o[e]
                    } else if (8 & i) {
                        const r = e.vnode.dynamicProps;
                        for (let a = 0; a < r.length; a++) {
                            const i = r[a],
                                c = t[i];
                            if (l)
                                if (P(o, i)) o[i] = c;
                                else {
                                    const t = j(i);
                                    n[t] = er(l, s, t, c, e)
                                }
                            else o[i] = c
                        }
                    }
                    le(e, "set", "$attrs")
                }(e, t.props, a, r), ((e, t) => {
                    const {
                        vnode: r,
                        slots: a
                    } = e;
                    let n = !0,
                        o = h;
                    if (32 & r.shapeFlag) {
                        const e = t._;
                        e ? 1 === e ? n = !1 : b(a, t) : (n = !t.$stable, Lr(t, a)), o = t
                    } else t && (Nr(e, t), o = {
                        default: 1
                    });
                    if (n)
                        for (const e in a) $r(e) || e in o || delete a[e]
                })(e, t.children), Tt(void 0, e.update)
        }, B = (e, t, r, a, n, o, i, s = !1) => {
            const l = e && e.children,
                c = e ? e.shapeFlag : 0,
                d = t.children,
                {
                    patchFlag: h,
                    shapeFlag: p
                } = t;
            if (h > 0) {
                if (128 & h) return void X(l, d, r, a, n, o, i, s);
                if (256 & h) return void z(l, d, r, a, n, o, i, s)
            }
            8 & p ? (16 & c && re(l, n, o), d !== l && u(r, d)) : 16 & c ? 16 & p ? X(l, d, r, a, n, o, i, s) : re(l, n, o, !0) : (8 & c && u(r, ""), 16 & p && O(d, r, a, n, o, i, s))
        }, z = (e, t, r, a, n, o, i, s) => {
            t = t || p;
            const l = (e = e || p).length,
                c = t.length,
                u = Math.min(l, c);
            let d;
            for (d = 0; d < u; d++) {
                const a = t[d] = s ? Ca(t[d]) : Sa(t[d]);
                w(e[d], a, r, null, n, o, i, s)
            }
            l > c ? re(e, n, o, !0, !1, u) : O(t, r, a, n, o, i, s, u)
        }, X = (e, t, r, a, n, o, i, s) => {
            let l = 0;
            const c = t.length;
            let u = e.length - 1,
                d = c - 1;
            for (; l <= u && l <= d;) {
                const a = e[l],
                    c = t[l] = s ? Ca(t[l]) : Sa(t[l]);
                if (!va(a, c)) break;
                w(a, c, r, null, n, o, i, s), l++
            }
            for (; l <= u && l <= d;) {
                const a = e[u],
                    l = t[d] = s ? Ca(t[d]) : Sa(t[d]);
                if (!va(a, l)) break;
                w(a, l, r, null, n, o, i, s), u--, d--
            }
            if (l > u) {
                if (l <= d) {
                    const e = d + 1,
                        u = e < c ? t[e].el : a;
                    for (; l <= d;) w(null, t[l] = s ? Ca(t[l]) : Sa(t[l]), r, u, n, o, i), l++
                }
            } else if (l > d)
                for (; l <= u;) G(e[l], n, o, !0), l++;
            else {
                const h = l,
                    f = l,
                    m = new Map;
                for (l = f; l <= d; l++) {
                    const e = t[l] = s ? Ca(t[l]) : Sa(t[l]);
                    null != e.key && m.set(e.key, l)
                }
                let v, g = 0;
                const y = d - f + 1;
                let b = !1,
                    E = 0;
                const P = new Array(y);
                for (l = 0; l < y; l++) P[l] = 0;
                for (l = h; l <= u; l++) {
                    const a = e[l];
                    if (g >= y) {
                        G(a, n, o, !0);
                        continue
                    }
                    let c;
                    if (null != a.key) c = m.get(a.key);
                    else
                        for (v = f; v <= d; v++)
                            if (0 === P[v - f] && va(a, t[v])) {
                                c = v;
                                break
                            } void 0 === c ? G(a, n, o, !0) : (P[c - f] = l + 1, c >= E ? E = c : b = !0, w(a, t[c], r, null, n, o, i, s), g++)
                }
                const k = b ? function(e) {
                    const t = e.slice(),
                        r = [0];
                    let a, n, o, i, s;
                    const l = e.length;
                    for (a = 0; a < l; a++) {
                        const l = e[a];
                        if (0 !== l) {
                            if (n = r[r.length - 1], e[n] < l) {
                                t[a] = n, r.push(a);
                                continue
                            }
                            for (o = 0, i = r.length - 1; o < i;) s = (o + i) / 2 | 0, e[r[s]] < l ? o = s + 1 : i = s;
                            l < e[r[o]] && (o > 0 && (t[a] = r[o - 1]), r[o] = a)
                        }
                    }
                    o = r.length, i = r[o - 1];
                    for (; o-- > 0;) r[o] = i, i = t[i];
                    return r
                }(P) : p;
                for (v = k.length - 1, l = y - 1; l >= 0; l--) {
                    const e = f + l,
                        s = t[e],
                        u = e + 1 < c ? t[e + 1].el : a;
                    0 === P[l] ? w(null, s, r, u, n, o, i) : b && (v < 0 || l !== k[v] ? Q(s, r, u, 2) : v--)
                }
            }
        }, Q = (e, t, a, n, o = null) => {
            const {
                el: i,
                type: s,
                transition: l,
                children: c,
                shapeFlag: u
            } = e;
            if (6 & u) return void Q(e.component.subTree, t, a, n);
            if (128 & u) return void e.suspense.move(t, a, n);
            if (64 & u) return void s.move(e, t, a, se);
            if (s === ia) {
                r(i, t, a);
                for (let e = 0; e < c.length; e++) Q(c[e], t, a, n);
                return void r(e.anchor, t, a)
            }
            if (s === ca) return void S(e, t, a);
            if (2 !== n && 1 & u && l)
                if (0 === n) l.beforeEnter(i), r(i, t, a), Wr((() => l.enter(i)), o);
                else {
                    const {
                        leave: e,
                        delayLeave: n,
                        afterLeave: o
                    } = l, s = () => r(i, t, a), c = () => {
                        e(i, (() => {
                            s(), o && o()
                        }))
                    };
                    n ? n(i, s, c) : c()
                }
            else r(i, t, a)
        }, G = (e, t, r, a = !1, n = !1) => {
            const {
                type: o,
                props: i,
                ref: s,
                children: l,
                dynamicChildren: c,
                shapeFlag: u,
                patchFlag: d,
                dirs: h
            } = e;
            if (null != s && Vr(s, null, r, null), 256 & u) return void t.ctx.deactivate(e);
            const p = 1 & u && h;
            let f;
            if ((f = i && i.onVnodeBeforeUnmount) && Xr(f, t, e), 6 & u) te(e.component, r, a);
            else {
                if (128 & u) return void e.suspense.unmount(r, a);
                p && jr(e, null, t, "beforeUnmount"), c && (o !== ia || d > 0 && 64 & d) ? re(c, t, r, !1, !0) : (o === ia && (128 & d || 256 & d) || !n && 16 & u) && re(l, t, r), 64 & u && (a || !Gr(e.props)) && e.type.remove(e, se), a && K(e)
            }((f = i && i.onVnodeUnmounted) || p) && Wr((() => {
                f && Xr(f, t, e), p && jr(e, null, t, "unmounted")
            }), r)
        }, K = e => {
            const {
                type: t,
                el: r,
                anchor: n,
                transition: o
            } = e;
            if (t === ia) return void J(r, n);
            if (t === ca) return void C(e);
            const i = () => {
                a(r), o && !o.persisted && o.afterLeave && o.afterLeave()
            };
            if (1 & e.shapeFlag && o && !o.persisted) {
                const {
                    leave: t,
                    delayLeave: a
                } = o, n = () => t(r, i);
                a ? a(e.el, i, n) : n()
            } else i()
        }, J = (e, t) => {
            let r;
            for (; e !== t;) r = m(e), a(e), e = r;
            a(t)
        }, te = (e, t, r) => {
            const {
                bum: a,
                effects: n,
                update: o,
                subTree: i,
                um: s
            } = e;
            if (a && W(a), n)
                for (let e = 0; e < n.length; e++) ee(n[e]);
            o && (ee(o), G(i, e, t, r)), s && Wr(s, t), Wr((() => {
                e.isUnmounted = !0
            }), t), t && t.pendingBranch && !t.isUnmounted && e.asyncDep && !e.asyncResolved && e.suspenseId === t.pendingId && (t.deps--, 0 === t.deps && t.resolve())
        }, re = (e, t, r, a = !1, n = !1, o = 0) => {
            for (let i = o; i < e.length; i++) G(e[i], t, r, a, n)
        }, ae = e => 6 & e.shapeFlag ? ae(e.component.subTree) : 128 & e.shapeFlag ? e.suspense.next() : m(e.anchor || e.el), ne = (e, t) => {
            null == e ? t._vnode && G(t._vnode, null, null, !0) : w(t._vnode || null, e, t), xt(), t._vnode = e
        }, se = {
            p: w,
            um: G,
            m: Q,
            r: K,
            mt: I,
            mc: O,
            pc: B,
            pbc: $,
            n: ae,
            o: e
        };
        let ce, ue;
        t && ([ce, ue] = t(se));
        return {
            render: ne,
            hydrate: ce,
            createApp: qr(ne, ce)
        }
    }(e)
}

function Xr(e, t, r, a = null) {
    lt(e, t, 7, [r, a])
}

function Qr(e, t, r = !1) {
    const a = e.children,
        n = t.children;
    if (k(a) && k(n))
        for (let e = 0; e < a.length; e++) {
            const t = a[e];
            let o = n[e];
            1 & o.shapeFlag && !o.dynamicChildren && ((o.patchFlag <= 0 || 32 === o.patchFlag) && (o = n[e] = Ca(n[e]), o.el = t.el), r || Qr(t, o))
        }
}
const Gr = e => e && (e.disabled || "" === e.disabled),
    Kr = e => "undefined" != typeof SVGElement && e instanceof SVGElement,
    Jr = (e, t) => {
        const r = e && e.to;
        if (x(r)) {
            if (t) {
                return t(r)
            }
            return null
        }
        return r
    };

function Zr(e, t, r, {
    o: {
        insert: a
    },
    m: n
}, o = 2) {
    0 === o && a(e.targetAnchor, t, r);
    const {
        el: i,
        anchor: s,
        shapeFlag: l,
        children: c,
        props: u
    } = e, d = 2 === o;
    if (d && a(i, t, r), (!d || Gr(u)) && 16 & l)
        for (let e = 0; e < c.length; e++) n(c[e], t, r, 2);
    d && a(s, t, r)
}
const ea = {
    __isTeleport: !0,
    process(e, t, r, a, n, o, i, s, l) {
        const {
            mc: c,
            pc: u,
            pbc: d,
            o: {
                insert: h,
                querySelector: p,
                createText: f,
                createComment: m
            }
        } = l, v = Gr(t.props), {
            shapeFlag: g,
            children: y
        } = t;
        if (null == e) {
            const e = t.el = f(""),
                l = t.anchor = f("");
            h(e, r, a), h(l, r, a);
            const u = t.target = Jr(t.props, p),
                d = t.targetAnchor = f("");
            u && (h(d, u), i = i || Kr(u));
            const m = (e, t) => {
                16 & g && c(y, e, t, n, o, i, s)
            };
            v ? m(r, l) : u && m(u, d)
        } else {
            t.el = e.el;
            const a = t.anchor = e.anchor,
                c = t.target = e.target,
                h = t.targetAnchor = e.targetAnchor,
                f = Gr(e.props),
                m = f ? r : c,
                g = f ? a : h;
            if (i = i || Kr(c), t.dynamicChildren ? (d(e.dynamicChildren, t.dynamicChildren, m, n, o, i), Qr(e, t, !0)) : s || u(e, t, m, g, n, o, i), v) f || Zr(t, r, a, l, 1);
            else if ((t.props && t.props.to) !== (e.props && e.props.to)) {
                const e = t.target = Jr(t.props, p);
                e && Zr(t, e, null, l, 0)
            } else f && Zr(t, c, h, l, 1)
        }
    },
    remove(e, {
        r: t,
        o: {
            remove: r
        }
    }) {
        const {
            shapeFlag: a,
            children: n,
            anchor: o
        } = e;
        if (r(o), 16 & a)
            for (let e = 0; e < n.length; e++) t(n[e])
    },
    move: Zr,
    hydrate: function(e, t, r, a, n, {
        o: {
            nextSibling: o,
            parentNode: i,
            querySelector: s
        }
    }, l) {
        const c = t.target = Jr(t.props, s);
        if (c) {
            const s = c._lpa || c.firstChild;
            16 & t.shapeFlag && (Gr(t.props) ? (t.anchor = l(o(e), t, i(e), r, a, n), t.targetAnchor = s) : (t.anchor = o(e), t.targetAnchor = l(s, t, c, r, a, n)), c._lpa = t.targetAnchor && o(t.targetAnchor))
        }
        return t.anchor && o(t.anchor)
    }
};

function ta(e) {
    return na("components", e) || e
}
const ra = Symbol();

function aa(e) {
    return x(e) ? na("components", e, !1) || e : e || ra
}

function na(e, t, r = !0) {
    const a = At || Wa;
    if (a) {
        const r = a.type;
        if ("components" === e) {
            if ("_self" === t) return r;
            const e = r.displayName || r.name;
            if (e && (e === t || e === j(t) || e === q(j(t)))) return r
        }
        return oa(a[e] || r[e], t) || oa(a.appContext[e], t)
    }
}

function oa(e, t) {
    return e && (e[t] || e[j(t)] || e[q(j(t))])
}
const ia = Symbol(void 0),
    sa = Symbol(void 0),
    la = Symbol(void 0),
    ca = Symbol(void 0),
    ua = [];
let da = null;

function ha(e = !1) {
    ua.push(da = e ? null : [])
}

function pa() {
    ua.pop(), da = ua[ua.length - 1] || null
}

function fa(e, t, r, a, n) {
    const o = wa(e, t, r, a, n, !0);
    return o.dynamicChildren = da || p, pa(), da && da.push(o), o
}

function ma(e) {
    return !!e && !0 === e.__v_isVNode
}

function va(e, t) {
    return e.type === t.type && e.key === t.key
}
const ga = "__vInternal",
    ya = ({
        key: e
    }) => null != e ? e : null,
    ba = ({
        ref: e
    }) => null != e ? x(e) || Je(e) || T(e) ? {
        i: At,
        r: e
    } : e : null,
    wa = function(e, t = null, r = null, n = 0, o = null, i = !1) {
        e && e !== ra || (e = la);
        if (ma(e)) {
            const a = Ea(e, t, !0);
            return r && Ta(a, r), a
        }
        l = e, T(l) && "__vccOpts" in l && (e = e.__vccOpts);
        var l;
        if (t) {
            (Qe(t) || ga in t) && (t = b({}, t));
            let {
                class: e,
                style: r
            } = t;
            e && !x(e) && (t.class = s(e)), O(r) && (Qe(r) && !k(r) && (r = b({}, r)), t.style = a(r))
        }
        const c = x(e) ? 1 : (e => e.__isSuspense)(e) ? 128 : (e => e.__isTeleport)(e) ? 64 : O(e) ? 4 : T(e) ? 2 : 0,
            u = {
                __v_isVNode: !0,
                __v_skip: !0,
                type: e,
                props: t,
                key: t && ya(t),
                ref: t && ba(t),
                scopeId: zt,
                children: null,
                component: null,
                suspense: null,
                ssContent: null,
                ssFallback: null,
                dirs: null,
                transition: null,
                el: null,
                anchor: null,
                target: null,
                targetAnchor: null,
                staticCount: 0,
                shapeFlag: c,
                patchFlag: n,
                dynamicProps: o,
                dynamicChildren: null,
                appContext: null
            };
        if (Ta(u, r), 128 & c) {
            const {
                content: e,
                fallback: t
            } = function(e) {
                const {
                    shapeFlag: t,
                    children: r
                } = e;
                let a, n;
                return 32 & t ? (a = Ht(r.default), n = Ht(r.fallback)) : (a = Ht(r), n = Sa(null)), {
                    content: a,
                    fallback: n
                }
            }(u);
            u.ssContent = e, u.ssFallback = t
        }!i && da && (n > 0 || 6 & c) && 32 !== n && da.push(u);
        return u
    };

function Ea(e, t, r = !1) {
    const {
        props: n,
        ref: o,
        patchFlag: i
    } = e, l = t ? function(...e) {
        const t = b({}, e[0]);
        for (let r = 1; r < e.length; r++) {
            const n = e[r];
            for (const e in n)
                if ("class" === e) t.class !== n.class && (t.class = s([t.class, n.class]));
                else if ("style" === e) t.style = a([t.style, n.style]);
            else if (g(e)) {
                const r = t[e],
                    a = n[e];
                r !== a && (t[e] = r ? [].concat(r, n[e]) : a)
            } else "" !== e && (t[e] = n[e])
        }
        return t
    }(n || {}, t) : n;
    return {
        __v_isVNode: !0,
        __v_skip: !0,
        type: e.type,
        props: l,
        key: l && ya(l),
        ref: t && t.ref ? r && o ? k(o) ? o.concat(ba(t)) : [o, ba(t)] : ba(t) : o,
        scopeId: e.scopeId,
        children: e.children,
        target: e.target,
        targetAnchor: e.targetAnchor,
        staticCount: e.staticCount,
        shapeFlag: e.shapeFlag,
        patchFlag: t && e.type !== ia ? -1 === i ? 16 : 16 | i : i,
        dynamicProps: e.dynamicProps,
        dynamicChildren: e.dynamicChildren,
        appContext: e.appContext,
        dirs: e.dirs,
        transition: e.transition,
        component: e.component,
        suspense: e.suspense,
        ssContent: e.ssContent && Ea(e.ssContent),
        ssFallback: e.ssFallback && Ea(e.ssFallback),
        el: e.el,
        anchor: e.anchor
    }
}

function Pa(e = " ", t = 0) {
    return wa(sa, null, e, t)
}

function ka(e, t) {
    const r = wa(ca, null, e);
    return r.staticCount = t, r
}

function _a(e = "", t = !1) {
    return t ? (ha(), fa(la, null, e)) : wa(la, null, e)
}

function Sa(e) {
    return null == e || "boolean" == typeof e ? wa(la) : k(e) ? wa(ia, null, e) : "object" == typeof e ? null === e.el ? e : Ea(e) : wa(sa, null, String(e))
}

function Ca(e) {
    return null === e.el ? e : Ea(e)
}

function Ta(e, t) {
    let r = 0;
    const {
        shapeFlag: a
    } = e;
    if (null == t) t = null;
    else if (k(t)) r = 16;
    else if ("object" == typeof t) {
        if (1 & a || 64 & a) {
            const r = t.default;
            return void(r && (r._c && Yt(1), Ta(e, r()), r._c && Yt(-1)))
        } {
            r = 32;
            const a = t._;
            a || ga in t ? 3 === a && At && (1024 & At.vnode.patchFlag ? (t._ = 2, e.patchFlag |= 1024) : t._ = 1) : t._ctx = At
        }
    } else T(t) ? (t = {
        default: t,
        _ctx: At
    }, r = 32) : (t = String(t), 64 & a ? (r = 16, t = [Pa(t)]) : r = 8);
    e.children = t, e.shapeFlag |= r
}

function xa(e, t) {
    if (Wa) {
        let r = Wa.provides;
        const a = Wa.parent && Wa.parent.provides;
        a === r && (r = Wa.provides = Object.create(a)), r[e] = t
    } else;
}

function Da(e, t, r = !1) {
    const a = Wa || At;
    if (a) {
        const n = null == a.parent ? a.vnode.appContext && a.vnode.appContext.provides : a.parent.provides;
        if (n && e in n) return n[e];
        if (arguments.length > 1) return r && T(t) ? t() : t
    }
}
let Oa = !1;

function Ra(e, t, r = [], a = [], n = [], o = !1) {
    const {
        mixins: i,
        extends: s,
        data: l,
        computed: c,
        methods: u,
        watch: d,
        provide: p,
        inject: m,
        components: v,
        directives: g,
        beforeMount: y,
        mounted: w,
        beforeUpdate: E,
        updated: P,
        activated: _,
        deactivated: S,
        beforeDestroy: C,
        beforeUnmount: x,
        destroyed: D,
        unmounted: R,
        render: F,
        renderTracked: $,
        renderTriggered: A,
        errorCaptured: M,
        expose: L
    } = t, N = e.proxy, I = e.ctx, j = e.appContext.mixins;
    if (o && F && e.render === f && (e.render = F), o || (Oa = !0, Fa("beforeCreate", "bc", t, e, j), Oa = !1, Ma(e, j, r, a, n)), s && Ra(e, s, r, a, n, !0), i && Ma(e, i, r, a, n), m)
        if (k(m))
            for (let e = 0; e < m.length; e++) {
                const t = m[e];
                I[t] = Da(t)
            } else
                for (const e in m) {
                    const t = m[e];
                    O(t) ? I[e] = Da(t.from || e, t.default, !0) : I[e] = Da(t)
                }
    if (u)
        for (const e in u) {
            const t = u[e];
            T(t) && (I[e] = t.bind(N))
        }
    if (o ? l && r.push(l) : (r.length && r.forEach((t => La(e, t, N))), l && La(e, l, N)), c)
        for (const e in c) {
            const t = c[e],
                r = Ja({
                    get: T(t) ? t.bind(N, N) : T(t.get) ? t.get.bind(N, N) : f,
                    set: !T(t) && T(t.set) ? t.set.bind(N) : f
                });
            Object.defineProperty(I, e, {
                enumerable: !0,
                configurable: !0,
                get: () => r.value,
                set: e => r.value = e
            })
        }
    var U;
    if (d && a.push(d), !o && a.length && a.forEach((e => {
            for (const t in e) Na(e[t], I, N, t)
        })), p && n.push(p), !o && n.length && n.forEach((e => {
            const t = T(e) ? e.call(N) : e;
            Reflect.ownKeys(t).forEach((e => {
                xa(e, t[e])
            }))
        })), o && (v && b(e.components || (e.components = b({}, e.type.components)), v), g && b(e.directives || (e.directives = b({}, e.type.directives)), g)), o || Fa("created", "c", t, e, j), y && lr(y.bind(N)), w && cr(w.bind(N)), E && ur(E.bind(N)), P && dr(P.bind(N)), _ && Rr(_.bind(N), "a", U), S && function(e, t) {
            Rr(e, "da", t)
        }(S.bind(N)), M && ((e, t = Wa) => {
            ir("ec", e, t)
        })(M.bind(N)), $ && mr($.bind(N)), A && fr(A.bind(N)), x && hr(x.bind(N)), R && pr(R.bind(N)), k(L) && !o)
        if (L.length) {
            const t = e.exposed || (e.exposed = nt({}));
            L.forEach((e => {
                t[e] = function(e, t) {
                    return Je(e[t]) ? e[t] : new ot(e, t)
                }(N, e)
            }))
        } else e.exposed || (e.exposed = h)
}

function Fa(e, t, r, a, n) {
    Aa(e, t, n, a);
    const {
        extends: o,
        mixins: i
    } = r;
    o && $a(e, t, o, a), i && Aa(e, t, i, a);
    const s = r[e];
    s && lt(s.bind(a.proxy), a, t)
}

function $a(e, t, r, a) {
    r.extends && $a(e, t, r.extends, a);
    const n = r[e];
    n && lt(n.bind(a.proxy), a, t)
}

function Aa(e, t, r, a) {
    for (let n = 0; n < r.length; n++) {
        const o = r[n].mixins;
        o && Aa(e, t, o, a);
        const i = r[n][e];
        i && lt(i.bind(a.proxy), a, t)
    }
}

function Ma(e, t, r, a, n) {
    for (let o = 0; o < t.length; o++) Ra(e, t[o], r, a, n, !0)
}

function La(e, t, r) {
    const a = t.call(r, r);
    O(a) && (e.data === h ? e.data = Be(a) : b(e.data, a))
}

function Na(e, t, r, a) {
    const n = a.includes(".") ? function(e, t) {
        const r = t.split(".");
        return () => {
            let t = e;
            for (let e = 0; e < r.length && t; e++) t = t[r[e]];
            return t
        }
    }(r, a) : () => r[a];
    if (x(e)) {
        const r = t[e];
        T(r) && yr(n, r)
    } else if (T(e)) yr(n, e.bind(r));
    else if (O(e))
        if (k(e)) e.forEach((e => Na(e, t, r, a)));
        else {
            const a = T(e.handler) ? e.handler.bind(r) : t[e.handler];
            T(a) && yr(n, a, e)
        }
}

function Ia(e, t, r) {
    const a = r.appContext.config.optionMergeStrategies,
        {
            mixins: n,
            extends: o
        } = t;
    o && Ia(e, o, r), n && n.forEach((t => Ia(e, t, r)));
    for (const n in t) a && P(a, n) ? e[n] = a[n](e[n], t[n], r.proxy, n) : e[n] = t[n]
}
const ja = e => e && (e.proxy ? e.proxy : ja(e.parent)),
    Ua = b(Object.create(null), {
        $: e => e,
        $el: e => e.vnode.el,
        $data: e => e.data,
        $props: e => e.props,
        $attrs: e => e.attrs,
        $slots: e => e.slots,
        $refs: e => e.refs,
        $parent: e => ja(e.parent),
        $root: e => e.root && e.root.proxy,
        $emit: e => e.emit,
        $options: e => function(e) {
            const t = e.type,
                {
                    __merged: r,
                    mixins: a,
                    extends: n
                } = t;
            if (r) return r;
            const o = e.appContext.mixins;
            if (!o.length && !a && !n) return t;
            const i = {};
            return o.forEach((t => Ia(i, t, e))), Ia(i, t, e), t.__merged = i
        }(e),
        $forceUpdate: e => () => _t(e.update),
        $nextTick: e => kt.bind(e.proxy),
        $watch: e => wr.bind(e)
    }),
    Ha = {
        get({
            _: e
        }, t) {
            const {
                ctx: r,
                setupState: a,
                data: n,
                props: o,
                accessCache: i,
                type: s,
                appContext: l
            } = e;
            if ("__v_skip" === t) return !0;
            let c;
            if ("$" !== t[0]) {
                const s = i[t];
                if (void 0 !== s) switch (s) {
                    case 0:
                        return a[t];
                    case 1:
                        return n[t];
                    case 3:
                        return r[t];
                    case 2:
                        return o[t]
                } else {
                    if (a !== h && P(a, t)) return i[t] = 0, a[t];
                    if (n !== h && P(n, t)) return i[t] = 1, n[t];
                    if ((c = e.propsOptions[0]) && P(c, t)) return i[t] = 2, o[t];
                    if (r !== h && P(r, t)) return i[t] = 3, r[t];
                    Oa || (i[t] = 4)
                }
            }
            const u = Ua[t];
            let d, p;
            return u ? ("$attrs" === t && se(e, 0, t), u(e)) : (d = s.__cssModules) && (d = d[t]) ? d : r !== h && P(r, t) ? (i[t] = 3, r[t]) : (p = l.config.globalProperties, P(p, t) ? p[t] : void 0)
        },
        set({
            _: e
        }, t, r) {
            const {
                data: a,
                setupState: n,
                ctx: o
            } = e;
            if (n !== h && P(n, t)) n[t] = r;
            else if (a !== h && P(a, t)) a[t] = r;
            else if (t in e.props) return !1;
            return ("$" !== t[0] || !(t.slice(1) in e)) && (o[t] = r, !0)
        },
        has({
            _: {
                data: e,
                setupState: t,
                accessCache: r,
                ctx: a,
                appContext: n,
                propsOptions: o
            }
        }, i) {
            let s;
            return void 0 !== r[i] || e !== h && P(e, i) || t !== h && P(t, i) || (s = o[0]) && P(s, i) || P(a, i) || P(Ua, i) || P(n.config.globalProperties, i)
        }
    },
    qa = b({}, Ha, {
        get(e, t) {
            if (t !== Symbol.unscopables) return Ha.get(e, t, e)
        },
        has: (e, r) => "_" !== r[0] && !t(r)
    }),
    Ya = Ur();
let Ba = 0;
let Wa = null;
const Va = () => Wa || At,
    za = e => {
        Wa = e
    };
let Xa = !1;

function Qa(e, t, r) {
    T(t) ? e.render = t : O(t) && (e.setupState = nt(t)), Ga(e)
}

function Ga(e, t) {
    const r = e.type;
    e.render || (e.render = r.render || f, e.render._rc && (e.withProxy = new Proxy(e.ctx, qa))), Wa = e, oe(), Ra(e, r), ie(), Wa = null
}

function Ka(e, t = Wa) {
    t && (t.effects || (t.effects = [])).push(e)
}

function Ja(e) {
    const t = function(e) {
        let t, r;
        return T(e) ? (t = e, r = f) : (t = e.get, r = e.set), new it(t, r, T(e) || !e.set)
    }(e);
    return Ka(t.effect), t
}

function Za(e, t, r) {
    const a = arguments.length;
    return 2 === a ? O(t) && !k(t) ? ma(t) ? wa(e, null, [t]) : wa(e, t) : wa(e, null, t) : (a > 3 ? r = Array.prototype.slice.call(arguments, 2) : 3 === a && ma(r) && (r = [r]), wa(e, t, r))
}

function en(e, t) {
    let r;
    if (k(e) || x(e)) {
        r = new Array(e.length);
        for (let a = 0, n = e.length; a < n; a++) r[a] = t(e[a], a)
    } else if ("number" == typeof e) {
        r = new Array(e);
        for (let a = 0; a < e; a++) r[a] = t(a + 1, a)
    } else if (O(e))
        if (e[Symbol.iterator]) r = Array.from(e, t);
        else {
            const a = Object.keys(e);
            r = new Array(a.length);
            for (let n = 0, o = a.length; n < o; n++) {
                const o = a[n];
                r[n] = t(e[o], o, n)
            }
        }
    else r = [];
    return r
}
const tn = "3.0.4",
    rn = "http://www.w3.org/2000/svg",
    an = "undefined" != typeof document ? document : null;
let nn, on;
const sn = {
    insert: (e, t, r) => {
        t.insertBefore(e, r || null)
    },
    remove: e => {
        const t = e.parentNode;
        t && t.removeChild(e)
    },
    createElement: (e, t, r) => t ? an.createElementNS(rn, e) : an.createElement(e, r ? {
        is: r
    } : void 0),
    createText: e => an.createTextNode(e),
    createComment: e => an.createComment(e),
    setText: (e, t) => {
        e.nodeValue = t
    },
    setElementText: (e, t) => {
        e.textContent = t
    },
    parentNode: e => e.parentNode,
    nextSibling: e => e.nextSibling,
    querySelector: e => an.querySelector(e),
    setScopeId(e, t) {
        e.setAttribute(t, "")
    },
    cloneNode: e => e.cloneNode(!0),
    insertStaticContent(e, t, r, a) {
        const n = a ? on || (on = an.createElementNS(rn, "svg")) : nn || (nn = an.createElement("div"));
        n.innerHTML = e;
        const o = n.firstChild;
        let i = o,
            s = i;
        for (; i;) s = i, sn.insert(i, t, r), i = n.firstChild;
        return [o, s]
    }
};
const ln = /\s*!important$/;

function cn(e, t, r) {
    if (k(r)) r.forEach((r => cn(e, t, r)));
    else if (t.startsWith("--")) e.setProperty(t, r);
    else {
        const a = function(e, t) {
            const r = dn[t];
            if (r) return r;
            let a = j(t);
            if ("filter" !== a && a in e) return dn[t] = a;
            a = q(a);
            for (let r = 0; r < un.length; r++) {
                const n = un[r] + a;
                if (n in e) return dn[t] = n
            }
            return t
        }(e, t);
        ln.test(r) ? e.setProperty(H(a), r.replace(ln, ""), "important") : e[a] = r
    }
}
const un = ["Webkit", "Moz", "ms"],
    dn = {};
const hn = "http://www.w3.org/1999/xlink";
let pn = Date.now;
"undefined" != typeof document && pn() > document.createEvent("Event").timeStamp && (pn = () => performance.now());
let fn = 0;
const mn = Promise.resolve(),
    vn = () => {
        fn = 0
    };

function gn(e, t, r, a) {
    e.addEventListener(t, r, a)
}

function yn(e, t, r, a, n = null) {
    const o = e._vei || (e._vei = {}),
        i = o[t];
    if (a && i) i.value = a;
    else {
        const [r, s] = function(e) {
            let t;
            if (bn.test(e)) {
                let r;
                for (t = {}; r = e.match(bn);) e = e.slice(0, e.length - r[0].length), t[r[0].toLowerCase()] = !0
            }
            return [e.slice(2).toLowerCase(), t]
        }(t);
        if (a) {
            gn(e, r, o[t] = function(e, t) {
                const r = e => {
                    (e.timeStamp || pn()) >= r.attached - 1 && lt(function(e, t) {
                        if (k(t)) {
                            const r = e.stopImmediatePropagation;
                            return e.stopImmediatePropagation = () => {
                                r.call(e), e._stopped = !0
                            }, t.map((e => t => !t._stopped && e(t)))
                        }
                        return t
                    }(e, r.value), t, 5, [e])
                };
                return r.value = e, r.attached = (() => fn || (mn.then(vn), fn = pn()))(), r
            }(a, n), s)
        } else i && (! function(e, t, r, a) {
            e.removeEventListener(t, r, a)
        }(e, r, i, s), o[t] = void 0)
    }
}
const bn = /(?:Once|Passive|Capture)$/;
const wn = /^on[a-z]/;
const En = "transition",
    Pn = (e, {
        slots: t
    }) => Za(kr, function(e) {
        let {
            name: t = "v",
            type: r,
            css: a = !0,
            duration: n,
            enterFromClass: o = `${t}-enter-from`,
            enterActiveClass: i = `${t}-enter-active`,
            enterToClass: s = `${t}-enter-to`,
            appearFromClass: l = o,
            appearActiveClass: c = i,
            appearToClass: u = s,
            leaveFromClass: d = `${t}-leave-from`,
            leaveActiveClass: h = `${t}-leave-active`,
            leaveToClass: p = `${t}-leave-to`
        } = e;
        const f = {};
        for (const t in e) t in kn || (f[t] = e[t]);
        if (!a) return f;
        const m = function(e) {
                if (null == e) return null;
                if (O(e)) return [_n(e.enter), _n(e.leave)]; {
                    const t = _n(e);
                    return [t, t]
                }
            }(n),
            v = m && m[0],
            g = m && m[1],
            {
                onBeforeEnter: y,
                onEnter: w,
                onEnterCancelled: E,
                onLeave: P,
                onLeaveCancelled: k,
                onBeforeAppear: _ = y,
                onAppear: S = w,
                onAppearCancelled: C = E
            } = f,
            T = (e, t, r) => {
                Cn(e, t ? u : s), Cn(e, t ? c : i), r && r()
            },
            x = (e, t) => {
                Cn(e, p), Cn(e, h), t && t()
            },
            D = e => (t, a) => {
                const n = e ? S : w,
                    i = () => T(t, e, a);
                n && n(t, i), Tn((() => {
                    Cn(t, e ? l : o), Sn(t, e ? u : s), n && n.length > 1 || Dn(t, r, v, i)
                }))
            };
        return b(f, {
            onBeforeEnter(e) {
                y && y(e), Sn(e, i), Sn(e, o)
            },
            onBeforeAppear(e) {
                _ && _(e), Sn(e, c), Sn(e, l)
            },
            onEnter: D(!1),
            onAppear: D(!0),
            onLeave(e, t) {
                const a = () => x(e, t);
                Sn(e, h), Sn(e, d);
                const n = e.style.transitionProperty;
                e.style.transitionProperty = "none", Tn((() => {
                    e.style.transitionProperty = n, Cn(e, d), Sn(e, p), P && P.length > 1 || Dn(e, r, g, a)
                })), P && P(e, a)
            },
            onEnterCancelled(e) {
                T(e, !1), E && E(e)
            },
            onAppearCancelled(e) {
                T(e, !0), C && C(e)
            },
            onLeaveCancelled(e) {
                x(e), k && k(e)
            }
        })
    }(e), t);
Pn.displayName = "Transition";
const kn = {
    name: String,
    type: String,
    css: {
        type: Boolean,
        default: !0
    },
    duration: [String, Number, Object],
    enterFromClass: String,
    enterActiveClass: String,
    enterToClass: String,
    appearFromClass: String,
    appearActiveClass: String,
    appearToClass: String,
    leaveFromClass: String,
    leaveActiveClass: String,
    leaveToClass: String
};
Pn.props = b({}, kr.props, kn);

function _n(e) {
    return z(e)
}

function Sn(e, t) {
    t.split(/\s+/).forEach((t => t && e.classList.add(t))), (e._vtc || (e._vtc = new Set)).add(t)
}

function Cn(e, t) {
    t.split(/\s+/).forEach((t => t && e.classList.remove(t)));
    const {
        _vtc: r
    } = e;
    r && (r.delete(t), r.size || (e._vtc = void 0))
}

function Tn(e) {
    requestAnimationFrame((() => {
        requestAnimationFrame(e)
    }))
}
let xn = 0;

function Dn(e, t, r, a) {
    const n = e._endId = ++xn,
        o = () => {
            n === e._endId && a()
        };
    if (r) return setTimeout(o, r);
    const {
        type: i,
        timeout: s,
        propCount: l
    } = function(e, t) {
        const r = window.getComputedStyle(e),
            a = e => (r[e] || "").split(", "),
            n = a("transitionDelay"),
            o = a("transitionDuration"),
            i = On(n, o),
            s = a("animationDelay"),
            l = a("animationDuration"),
            c = On(s, l);
        let u = null,
            d = 0,
            h = 0;
        t === En ? i > 0 && (u = En, d = i, h = o.length) : "animation" === t ? c > 0 && (u = "animation", d = c, h = l.length) : (d = Math.max(i, c), u = d > 0 ? i > c ? En : "animation" : null, h = u ? u === En ? o.length : l.length : 0);
        const p = u === En && /\b(transform|all)(,|$)/.test(r.transitionProperty);
        return {
            type: u,
            timeout: d,
            propCount: h,
            hasTransform: p
        }
    }(e, t);
    if (!i) return a();
    const c = i + "end";
    let u = 0;
    const d = () => {
            e.removeEventListener(c, h), o()
        },
        h = t => {
            t.target === e && ++u >= l && d()
        };
    setTimeout((() => {
        u < l && d()
    }), s + 1), e.addEventListener(c, h)
}

function On(e, t) {
    for (; e.length < t.length;) e = e.concat(e);
    return Math.max(...t.map(((t, r) => Rn(t) + Rn(e[r]))))
}

function Rn(e) {
    return 1e3 * Number(e.slice(0, -1).replace(",", "."))
}
const Fn = e => {
    const t = e.props["onUpdate:modelValue"];
    return k(t) ? e => W(t, e) : t
};

function $n(e) {
    e.target.composing = !0
}

function An(e) {
    const t = e.target;
    t.composing && (t.composing = !1, function(e, t) {
        const r = document.createEvent("HTMLEvents");
        r.initEvent(t, !0, !0), e.dispatchEvent(r)
    }(t, "input"))
}
const Mn = {
        created(e, {
            modifiers: {
                lazy: t,
                trim: r,
                number: a
            }
        }, n) {
            e._assign = Fn(n);
            const o = a || "number" === e.type;
            gn(e, t ? "change" : "input", (t => {
                if (t.target.composing) return;
                let a = e.value;
                r ? a = a.trim() : o && (a = z(a)), e._assign(a)
            })), r && gn(e, "change", (() => {
                e.value = e.value.trim()
            })), t || (gn(e, "compositionstart", $n), gn(e, "compositionend", An), gn(e, "change", An))
        },
        mounted(e, {
            value: t
        }) {
            e.value = null == t ? "" : t
        },
        beforeUpdate(e, {
            value: t,
            modifiers: {
                trim: r,
                number: a
            }
        }, n) {
            if (e._assign = Fn(n), e.composing) return;
            if (document.activeElement === e) {
                if (r && e.value.trim() === t) return;
                if ((a || "number" === e.type) && z(e.value) === t) return
            }
            const o = null == t ? "" : t;
            e.value !== o && (e.value = o)
        }
    },
    Ln = {
        created(e, {
            value: t,
            modifiers: {
                number: r
            }
        }, a) {
            const n = S(t);
            gn(e, "change", (() => {
                const t = Array.prototype.filter.call(e.options, (e => e.selected)).map((e => r ? z(In(e)) : In(e)));
                e._assign(e.multiple ? n ? new Set(t) : t : t[0])
            })), e._assign = Fn(a)
        },
        mounted(e, {
            value: t
        }) {
            Nn(e, t)
        },
        beforeUpdate(e, t, r) {
            e._assign = Fn(r)
        },
        updated(e, {
            value: t
        }) {
            Nn(e, t)
        }
    };

function Nn(e, t) {
    const r = e.multiple;
    if (!r || k(t) || S(t)) {
        for (let a = 0, n = e.options.length; a < n; a++) {
            const n = e.options[a],
                o = In(n);
            if (r) k(t) ? n.selected = c(t, o) > -1 : n.selected = t.has(o);
            else if (l(In(n), t)) return void(e.selectedIndex = a)
        }
        r || (e.selectedIndex = -1)
    }
}

function In(e) {
    return "_value" in e ? e._value : e.value
}
const jn = ["ctrl", "shift", "alt", "meta"],
    Un = {
        stop: e => e.stopPropagation(),
        prevent: e => e.preventDefault(),
        self: e => e.target !== e.currentTarget,
        ctrl: e => !e.ctrlKey,
        shift: e => !e.shiftKey,
        alt: e => !e.altKey,
        meta: e => !e.metaKey,
        left: e => "button" in e && 0 !== e.button,
        middle: e => "button" in e && 1 !== e.button,
        right: e => "button" in e && 2 !== e.button,
        exact: (e, t) => jn.some((r => e[`${r}Key`] && !t.includes(r)))
    },
    Hn = (e, t) => (r, ...a) => {
        for (let e = 0; e < t.length; e++) {
            const a = Un[t[e]];
            if (a && a(r, t)) return
        }
        return e(r, ...a)
    },
    qn = {
        esc: "escape",
        space: " ",
        up: "arrow-up",
        left: "arrow-left",
        right: "arrow-right",
        down: "arrow-down",
        delete: "backspace"
    },
    Yn = (e, t) => r => {
        if (!("key" in r)) return;
        const a = H(r.key);
        return t.some((e => e === a || qn[e] === a)) ? e(r) : void 0
    },
    Bn = {
        beforeMount(e, {
            value: t
        }, {
            transition: r
        }) {
            e._vod = "none" === e.style.display ? "" : e.style.display, r && t ? r.beforeEnter(e) : Wn(e, t)
        },
        mounted(e, {
            value: t
        }, {
            transition: r
        }) {
            r && t && r.enter(e)
        },
        updated(e, {
            value: t,
            oldValue: r
        }, {
            transition: a
        }) {
            a && t !== r ? t ? (a.beforeEnter(e), Wn(e, !0), a.enter(e)) : a.leave(e, (() => {
                Wn(e, !1)
            })) : Wn(e, t)
        },
        beforeUnmount(e, {
            value: t
        }) {
            Wn(e, t)
        }
    };

function Wn(e, t) {
    e.style.display = t ? e._vod : "none"
}
const Vn = b({
    patchProp: (e, t, a, n, o = !1, i, s, l, c) => {
        switch (t) {
            case "class":
                ! function(e, t, r) {
                    if (null == t && (t = ""), r) e.setAttribute("class", t);
                    else {
                        const r = e._vtc;
                        r && (t = (t ? [t, ...r] : [...r]).join(" ")), e.className = t
                    }
                }(e, n, o);
                break;
            case "style":
                ! function(e, t, r) {
                    const a = e.style;
                    if (r)
                        if (x(r)) t !== r && (a.cssText = r);
                        else {
                            for (const e in r) cn(a, e, r[e]);
                            if (t && !x(t))
                                for (const e in t) null == r[e] && cn(a, e, "")
                        }
                    else e.removeAttribute("style")
                }(e, a, n);
                break;
            default:
                g(t) ? y(t) || yn(e, t, 0, n, s) : function(e, t, r, a) {
                    if (a) return "innerHTML" === t || !!(t in e && wn.test(t) && T(r));
                    if ("spellcheck" === t || "draggable" === t) return !1;
                    if ("form" === t && "string" == typeof r) return !1;
                    if ("list" === t && "INPUT" === e.tagName) return !1;
                    if (wn.test(t) && x(r)) return !1;
                    return t in e
                }(e, t, n, o) ? function(e, t, r, a, n, o, i) {
                    if ("innerHTML" === t || "textContent" === t) return a && i(a, n, o), void(e[t] = null == r ? "" : r);
                    if ("value" !== t || "PROGRESS" === e.tagName) {
                        if ("" === r || null == r) {
                            const a = typeof e[t];
                            if ("" === r && "boolean" === a) return void(e[t] = !0);
                            if (null == r && "string" === a) return e[t] = "", void e.removeAttribute(t);
                            if ("number" === a) return e[t] = 0, void e.removeAttribute(t)
                        }
                        try {
                            e[t] = r
                        } catch (e) {}
                    } else {
                        e._value = r;
                        const t = null == r ? "" : r;
                        e.value !== t && (e.value = t)
                    }
                }(e, t, n, i, s, l, c) : ("true-value" === t ? e._trueValue = n : "false-value" === t && (e._falseValue = n), function(e, t, a, n) {
                    if (n && t.startsWith("xlink:")) null == a ? e.removeAttributeNS(hn, t.slice(6, t.length)) : e.setAttributeNS(hn, t, a);
                    else {
                        const n = r(t);
                        null == a || n && !1 === a ? e.removeAttribute(t) : e.setAttribute(t, n ? "" : a)
                    }
                }(e, t, n, o))
        }
    },
    forcePatchProp: (e, t) => "value" === t
}, sn);
let zn;
/*!
 * perfect-scrollbar v1.5.0
 * Copyright 2020 Hyunje Jun, MDBootstrap and Contributors
 * Licensed under MIT
 */
function Xn(e) {
    return getComputedStyle(e)
}

function Qn(e, t) {
    for (var r in t) {
        var a = t[r];
        "number" == typeof a && (a += "px"), e.style[r] = a
    }
    return e
}

function Gn(e) {
    var t = document.createElement("div");
    return t.className = e, t
}
var Kn = "undefined" != typeof Element && (Element.prototype.matches || Element.prototype.webkitMatchesSelector || Element.prototype.mozMatchesSelector || Element.prototype.msMatchesSelector);

function Jn(e, t) {
    if (!Kn) throw new Error("No element matching method supported");
    return Kn.call(e, t)
}

function Zn(e) {
    e.remove ? e.remove() : e.parentNode && e.parentNode.removeChild(e)
}

function eo(e, t) {
    return Array.prototype.filter.call(e.children, (function(e) {
        return Jn(e, t)
    }))
}
var to = "ps",
    ro = "ps__rtl",
    ao = {
        thumb: function(e) {
            return "ps__thumb-" + e
        },
        rail: function(e) {
            return "ps__rail-" + e
        },
        consuming: "ps__child--consume"
    },
    no = {
        focus: "ps--focus",
        clicking: "ps--clicking",
        active: function(e) {
            return "ps--active-" + e
        },
        scrolling: function(e) {
            return "ps--scrolling-" + e
        }
    },
    oo = {
        x: null,
        y: null
    };

function io(e, t) {
    var r = e.element.classList,
        a = no.scrolling(t);
    r.contains(a) ? clearTimeout(oo[t]) : r.add(a)
}

function so(e, t) {
    oo[t] = setTimeout((function() {
        return e.isAlive && e.element.classList.remove(no.scrolling(t))
    }), e.settings.scrollingThreshold)
}
var lo = function(e) {
        this.element = e, this.handlers = {}
    },
    co = {
        isEmpty: {
            configurable: !0
        }
    };
lo.prototype.bind = function(e, t) {
    void 0 === this.handlers[e] && (this.handlers[e] = []), this.handlers[e].push(t), this.element.addEventListener(e, t, !1)
}, lo.prototype.unbind = function(e, t) {
    var r = this;
    this.handlers[e] = this.handlers[e].filter((function(a) {
        return !(!t || a === t) || (r.element.removeEventListener(e, a, !1), !1)
    }))
}, lo.prototype.unbindAll = function() {
    for (var e in this.handlers) this.unbind(e)
}, co.isEmpty.get = function() {
    var e = this;
    return Object.keys(this.handlers).every((function(t) {
        return 0 === e.handlers[t].length
    }))
}, Object.defineProperties(lo.prototype, co);
var uo = function() {
    this.eventElements = []
};

function ho(e) {
    if ("function" == typeof window.CustomEvent) return new CustomEvent(e);
    var t = document.createEvent("CustomEvent");
    return t.initCustomEvent(e, !1, !1, void 0), t
}

function po(e, t, r, a, n) {
    var o;
    if (void 0 === a && (a = !0), void 0 === n && (n = !1), "top" === t) o = ["contentHeight", "containerHeight", "scrollTop", "y", "up", "down"];
    else {
        if ("left" !== t) throw new Error("A proper axis should be provided");
        o = ["contentWidth", "containerWidth", "scrollLeft", "x", "left", "right"]
    }! function(e, t, r, a, n) {
        var o = r[0],
            i = r[1],
            s = r[2],
            l = r[3],
            c = r[4],
            u = r[5];
        void 0 === a && (a = !0);
        void 0 === n && (n = !1);
        var d = e.element;
        e.reach[l] = null, d[s] < 1 && (e.reach[l] = "start");
        d[s] > e[o] - e[i] - 1 && (e.reach[l] = "end");
        t && (d.dispatchEvent(ho("ps-scroll-" + l)), t < 0 ? d.dispatchEvent(ho("ps-scroll-" + c)) : t > 0 && d.dispatchEvent(ho("ps-scroll-" + u)), a && function(e, t) {
            io(e, t), so(e, t)
        }(e, l));
        e.reach[l] && (t || n) && d.dispatchEvent(ho("ps-" + l + "-reach-" + e.reach[l]))
    }(e, r, o, a, n)
}

function fo(e) {
    return parseInt(e, 10) || 0
}
uo.prototype.eventElement = function(e) {
    var t = this.eventElements.filter((function(t) {
        return t.element === e
    }))[0];
    return t || (t = new lo(e), this.eventElements.push(t)), t
}, uo.prototype.bind = function(e, t, r) {
    this.eventElement(e).bind(t, r)
}, uo.prototype.unbind = function(e, t, r) {
    var a = this.eventElement(e);
    a.unbind(t, r), a.isEmpty && this.eventElements.splice(this.eventElements.indexOf(a), 1)
}, uo.prototype.unbindAll = function() {
    this.eventElements.forEach((function(e) {
        return e.unbindAll()
    })), this.eventElements = []
}, uo.prototype.once = function(e, t, r) {
    var a = this.eventElement(e),
        n = function(e) {
            a.unbind(t, n), r(e)
        };
    a.bind(t, n)
};
var mo = {
    isWebKit: "undefined" != typeof document && "WebkitAppearance" in document.documentElement.style,
    supportsTouch: "undefined" != typeof window && ("ontouchstart" in window || "maxTouchPoints" in window.navigator && window.navigator.maxTouchPoints > 0 || window.DocumentTouch && document instanceof window.DocumentTouch),
    supportsIePointer: "undefined" != typeof navigator && navigator.msMaxTouchPoints,
    isChrome: "undefined" != typeof navigator && /Chrome/i.test(navigator && navigator.userAgent)
};

function vo(e) {
    var t = e.element,
        r = Math.floor(t.scrollTop),
        a = t.getBoundingClientRect();
    e.containerWidth = Math.ceil(a.width), e.containerHeight = Math.ceil(a.height), e.contentWidth = t.scrollWidth, e.contentHeight = t.scrollHeight, t.contains(e.scrollbarXRail) || (eo(t, ao.rail("x")).forEach((function(e) {
            return Zn(e)
        })), t.appendChild(e.scrollbarXRail)), t.contains(e.scrollbarYRail) || (eo(t, ao.rail("y")).forEach((function(e) {
            return Zn(e)
        })), t.appendChild(e.scrollbarYRail)), !e.settings.suppressScrollX && e.containerWidth + e.settings.scrollXMarginOffset < e.contentWidth ? (e.scrollbarXActive = !0, e.railXWidth = e.containerWidth - e.railXMarginWidth, e.railXRatio = e.containerWidth / e.railXWidth, e.scrollbarXWidth = go(e, fo(e.railXWidth * e.containerWidth / e.contentWidth)), e.scrollbarXLeft = fo((e.negativeScrollAdjustment + t.scrollLeft) * (e.railXWidth - e.scrollbarXWidth) / (e.contentWidth - e.containerWidth))) : e.scrollbarXActive = !1, !e.settings.suppressScrollY && e.containerHeight + e.settings.scrollYMarginOffset < e.contentHeight ? (e.scrollbarYActive = !0, e.railYHeight = e.containerHeight - e.railYMarginHeight, e.railYRatio = e.containerHeight / e.railYHeight, e.scrollbarYHeight = go(e, fo(e.railYHeight * e.containerHeight / e.contentHeight)), e.scrollbarYTop = fo(r * (e.railYHeight - e.scrollbarYHeight) / (e.contentHeight - e.containerHeight))) : e.scrollbarYActive = !1, e.scrollbarXLeft >= e.railXWidth - e.scrollbarXWidth && (e.scrollbarXLeft = e.railXWidth - e.scrollbarXWidth), e.scrollbarYTop >= e.railYHeight - e.scrollbarYHeight && (e.scrollbarYTop = e.railYHeight - e.scrollbarYHeight),
        function(e, t) {
            var r = {
                    width: t.railXWidth
                },
                a = Math.floor(e.scrollTop);
            t.isRtl ? r.left = t.negativeScrollAdjustment + e.scrollLeft + t.containerWidth - t.contentWidth : r.left = e.scrollLeft;
            t.isScrollbarXUsingBottom ? r.bottom = t.scrollbarXBottom - a : r.top = t.scrollbarXTop + a;
            Qn(t.scrollbarXRail, r);
            var n = {
                top: a,
                height: t.railYHeight
            };
            t.isScrollbarYUsingRight ? t.isRtl ? n.right = t.contentWidth - (t.negativeScrollAdjustment + e.scrollLeft) - t.scrollbarYRight - t.scrollbarYOuterWidth - 9 : n.right = t.scrollbarYRight - e.scrollLeft : t.isRtl ? n.left = t.negativeScrollAdjustment + e.scrollLeft + 2 * t.containerWidth - t.contentWidth - t.scrollbarYLeft - t.scrollbarYOuterWidth : n.left = t.scrollbarYLeft + e.scrollLeft;
            Qn(t.scrollbarYRail, n), Qn(t.scrollbarX, {
                left: t.scrollbarXLeft,
                width: t.scrollbarXWidth - t.railBorderXWidth
            }), Qn(t.scrollbarY, {
                top: t.scrollbarYTop,
                height: t.scrollbarYHeight - t.railBorderYWidth
            })
        }(t, e), e.scrollbarXActive ? t.classList.add(no.active("x")) : (t.classList.remove(no.active("x")), e.scrollbarXWidth = 0, e.scrollbarXLeft = 0, t.scrollLeft = !0 === e.isRtl ? e.contentWidth : 0), e.scrollbarYActive ? t.classList.add(no.active("y")) : (t.classList.remove(no.active("y")), e.scrollbarYHeight = 0, e.scrollbarYTop = 0, t.scrollTop = 0)
}

function go(e, t) {
    return e.settings.minScrollbarLength && (t = Math.max(t, e.settings.minScrollbarLength)), e.settings.maxScrollbarLength && (t = Math.min(t, e.settings.maxScrollbarLength)), t
}

function yo(e, t) {
    var r = t[0],
        a = t[1],
        n = t[2],
        o = t[3],
        i = t[4],
        s = t[5],
        l = t[6],
        c = t[7],
        u = t[8],
        d = e.element,
        h = null,
        p = null,
        f = null;

    function m(t) {
        t.touches && t.touches[0] && (t[n] = t.touches[0].pageY), d[l] = h + f * (t[n] - p), io(e, c), vo(e), t.stopPropagation(), t.preventDefault()
    }

    function v() {
        so(e, c), e[u].classList.remove(no.clicking), e.event.unbind(e.ownerDocument, "mousemove", m)
    }

    function g(t, i) {
        h = d[l], i && t.touches && (t[n] = t.touches[0].pageY), p = t[n], f = (e[a] - e[r]) / (e[o] - e[s]), i ? e.event.bind(e.ownerDocument, "touchmove", m) : (e.event.bind(e.ownerDocument, "mousemove", m), e.event.once(e.ownerDocument, "mouseup", v), t.preventDefault()), e[u].classList.add(no.clicking), t.stopPropagation()
    }
    e.event.bind(e[i], "mousedown", (function(e) {
        g(e)
    })), e.event.bind(e[i], "touchstart", (function(e) {
        g(e, !0)
    }))
}
var bo = {
        "click-rail": function(e) {
            e.element, e.event.bind(e.scrollbarY, "mousedown", (function(e) {
                return e.stopPropagation()
            })), e.event.bind(e.scrollbarYRail, "mousedown", (function(t) {
                var r = t.pageY - window.pageYOffset - e.scrollbarYRail.getBoundingClientRect().top > e.scrollbarYTop ? 1 : -1;
                e.element.scrollTop += r * e.containerHeight, vo(e), t.stopPropagation()
            })), e.event.bind(e.scrollbarX, "mousedown", (function(e) {
                return e.stopPropagation()
            })), e.event.bind(e.scrollbarXRail, "mousedown", (function(t) {
                var r = t.pageX - window.pageXOffset - e.scrollbarXRail.getBoundingClientRect().left > e.scrollbarXLeft ? 1 : -1;
                e.element.scrollLeft += r * e.containerWidth, vo(e), t.stopPropagation()
            }))
        },
        "drag-thumb": function(e) {
            yo(e, ["containerWidth", "contentWidth", "pageX", "railXWidth", "scrollbarX", "scrollbarXWidth", "scrollLeft", "x", "scrollbarXRail"]), yo(e, ["containerHeight", "contentHeight", "pageY", "railYHeight", "scrollbarY", "scrollbarYHeight", "scrollTop", "y", "scrollbarYRail"])
        },
        keyboard: function(e) {
            var t = e.element;
            e.event.bind(e.ownerDocument, "keydown", (function(r) {
                if (!(r.isDefaultPrevented && r.isDefaultPrevented() || r.defaultPrevented) && (Jn(t, ":hover") || Jn(e.scrollbarX, ":focus") || Jn(e.scrollbarY, ":focus"))) {
                    var a, n = document.activeElement ? document.activeElement : e.ownerDocument.activeElement;
                    if (n) {
                        if ("IFRAME" === n.tagName) n = n.contentDocument.activeElement;
                        else
                            for (; n.shadowRoot;) n = n.shadowRoot.activeElement;
                        if (Jn(a = n, "input,[contenteditable]") || Jn(a, "select,[contenteditable]") || Jn(a, "textarea,[contenteditable]") || Jn(a, "button,[contenteditable]")) return
                    }
                    var o = 0,
                        i = 0;
                    switch (r.which) {
                        case 37:
                            o = r.metaKey ? -e.contentWidth : r.altKey ? -e.containerWidth : -30;
                            break;
                        case 38:
                            i = r.metaKey ? e.contentHeight : r.altKey ? e.containerHeight : 30;
                            break;
                        case 39:
                            o = r.metaKey ? e.contentWidth : r.altKey ? e.containerWidth : 30;
                            break;
                        case 40:
                            i = r.metaKey ? -e.contentHeight : r.altKey ? -e.containerHeight : -30;
                            break;
                        case 32:
                            i = r.shiftKey ? e.containerHeight : -e.containerHeight;
                            break;
                        case 33:
                            i = e.containerHeight;
                            break;
                        case 34:
                            i = -e.containerHeight;
                            break;
                        case 36:
                            i = e.contentHeight;
                            break;
                        case 35:
                            i = -e.contentHeight;
                            break;
                        default:
                            return
                    }
                    e.settings.suppressScrollX && 0 !== o || e.settings.suppressScrollY && 0 !== i || (t.scrollTop -= i, t.scrollLeft += o, vo(e), function(r, a) {
                        var n = Math.floor(t.scrollTop);
                        if (0 === r) {
                            if (!e.scrollbarYActive) return !1;
                            if (0 === n && a > 0 || n >= e.contentHeight - e.containerHeight && a < 0) return !e.settings.wheelPropagation
                        }
                        var o = t.scrollLeft;
                        if (0 === a) {
                            if (!e.scrollbarXActive) return !1;
                            if (0 === o && r < 0 || o >= e.contentWidth - e.containerWidth && r > 0) return !e.settings.wheelPropagation
                        }
                        return !0
                    }(o, i) && r.preventDefault())
                }
            }))
        },
        wheel: function(e) {
            var t = e.element;

            function r(r) {
                var a = function(e) {
                        var t = e.deltaX,
                            r = -1 * e.deltaY;
                        return void 0 !== t && void 0 !== r || (t = -1 * e.wheelDeltaX / 6, r = e.wheelDeltaY / 6), e.deltaMode && 1 === e.deltaMode && (t *= 10, r *= 10), t != t && r != r && (t = 0, r = e.wheelDelta), e.shiftKey ? [-r, -t] : [t, r]
                    }(r),
                    n = a[0],
                    o = a[1];
                if (! function(e, r, a) {
                        if (!mo.isWebKit && t.querySelector("select:focus")) return !0;
                        if (!t.contains(e)) return !1;
                        for (var n = e; n && n !== t;) {
                            if (n.classList.contains(ao.consuming)) return !0;
                            var o = Xn(n);
                            if (a && o.overflowY.match(/(scroll|auto)/)) {
                                var i = n.scrollHeight - n.clientHeight;
                                if (i > 0 && (n.scrollTop > 0 && a < 0 || n.scrollTop < i && a > 0)) return !0
                            }
                            if (r && o.overflowX.match(/(scroll|auto)/)) {
                                var s = n.scrollWidth - n.clientWidth;
                                if (s > 0 && (n.scrollLeft > 0 && r < 0 || n.scrollLeft < s && r > 0)) return !0
                            }
                            n = n.parentNode
                        }
                        return !1
                    }(r.target, n, o)) {
                    var i = !1;
                    e.settings.useBothWheelAxes ? e.scrollbarYActive && !e.scrollbarXActive ? (o ? t.scrollTop -= o * e.settings.wheelSpeed : t.scrollTop += n * e.settings.wheelSpeed, i = !0) : e.scrollbarXActive && !e.scrollbarYActive && (n ? t.scrollLeft += n * e.settings.wheelSpeed : t.scrollLeft -= o * e.settings.wheelSpeed, i = !0) : (t.scrollTop -= o * e.settings.wheelSpeed, t.scrollLeft += n * e.settings.wheelSpeed), vo(e), (i = i || function(r, a) {
                        var n = Math.floor(t.scrollTop),
                            o = 0 === t.scrollTop,
                            i = n + t.offsetHeight === t.scrollHeight,
                            s = 0 === t.scrollLeft,
                            l = t.scrollLeft + t.offsetWidth === t.scrollWidth;
                        return !(Math.abs(a) > Math.abs(r) ? o || i : s || l) || !e.settings.wheelPropagation
                    }(n, o)) && !r.ctrlKey && (r.stopPropagation(), r.preventDefault())
                }
            }
            void 0 !== window.onwheel ? e.event.bind(t, "wheel", r) : void 0 !== window.onmousewheel && e.event.bind(t, "mousewheel", r)
        },
        touch: function(e) {
            if (mo.supportsTouch || mo.supportsIePointer) {
                var t = e.element,
                    r = {},
                    a = 0,
                    n = {},
                    o = null;
                mo.supportsTouch ? (e.event.bind(t, "touchstart", c), e.event.bind(t, "touchmove", u), e.event.bind(t, "touchend", d)) : mo.supportsIePointer && (window.PointerEvent ? (e.event.bind(t, "pointerdown", c), e.event.bind(t, "pointermove", u), e.event.bind(t, "pointerup", d)) : window.MSPointerEvent && (e.event.bind(t, "MSPointerDown", c), e.event.bind(t, "MSPointerMove", u), e.event.bind(t, "MSPointerUp", d)))
            }

            function i(r, a) {
                t.scrollTop -= a, t.scrollLeft -= r, vo(e)
            }

            function s(e) {
                return e.targetTouches ? e.targetTouches[0] : e
            }

            function l(e) {
                return (!e.pointerType || "pen" !== e.pointerType || 0 !== e.buttons) && (!(!e.targetTouches || 1 !== e.targetTouches.length) || !(!e.pointerType || "mouse" === e.pointerType || e.pointerType === e.MSPOINTER_TYPE_MOUSE))
            }

            function c(e) {
                if (l(e)) {
                    var t = s(e);
                    r.pageX = t.pageX, r.pageY = t.pageY, a = (new Date).getTime(), null !== o && clearInterval(o)
                }
            }

            function u(o) {
                if (l(o)) {
                    var c = s(o),
                        u = {
                            pageX: c.pageX,
                            pageY: c.pageY
                        },
                        d = u.pageX - r.pageX,
                        h = u.pageY - r.pageY;
                    if (function(e, r, a) {
                            if (!t.contains(e)) return !1;
                            for (var n = e; n && n !== t;) {
                                if (n.classList.contains(ao.consuming)) return !0;
                                var o = Xn(n);
                                if (a && o.overflowY.match(/(scroll|auto)/)) {
                                    var i = n.scrollHeight - n.clientHeight;
                                    if (i > 0 && (n.scrollTop > 0 && a < 0 || n.scrollTop < i && a > 0)) return !0
                                }
                                if (r && o.overflowX.match(/(scroll|auto)/)) {
                                    var s = n.scrollWidth - n.clientWidth;
                                    if (s > 0 && (n.scrollLeft > 0 && r < 0 || n.scrollLeft < s && r > 0)) return !0
                                }
                                n = n.parentNode
                            }
                            return !1
                        }(o.target, d, h)) return;
                    i(d, h), r = u;
                    var p = (new Date).getTime(),
                        f = p - a;
                    f > 0 && (n.x = d / f, n.y = h / f, a = p),
                        function(r, a) {
                            var n = Math.floor(t.scrollTop),
                                o = t.scrollLeft,
                                i = Math.abs(r),
                                s = Math.abs(a);
                            if (s > i) {
                                if (a < 0 && n === e.contentHeight - e.containerHeight || a > 0 && 0 === n) return 0 === window.scrollY && a > 0 && mo.isChrome
                            } else if (i > s && (r < 0 && o === e.contentWidth - e.containerWidth || r > 0 && 0 === o)) return !0;
                            return !0
                        }(d, h) && o.preventDefault()
                }
            }

            function d() {
                e.settings.swipeEasing && (clearInterval(o), o = setInterval((function() {
                    e.isInitialized ? clearInterval(o) : n.x || n.y ? Math.abs(n.x) < .01 && Math.abs(n.y) < .01 ? clearInterval(o) : (i(30 * n.x, 30 * n.y), n.x *= .8, n.y *= .8) : clearInterval(o)
                }), 10))
            }
        }
    },
    wo = function(e, t) {
        var r = this;
        if (void 0 === t && (t = {}), "string" == typeof e && (e = document.querySelector(e)), !e || !e.nodeName) throw new Error("no element is specified to initialize PerfectScrollbar");
        for (var a in this.element = e, e.classList.add(to), this.settings = {
                handlers: ["click-rail", "drag-thumb", "keyboard", "wheel", "touch"],
                maxScrollbarLength: null,
                minScrollbarLength: null,
                scrollingThreshold: 1e3,
                scrollXMarginOffset: 0,
                scrollYMarginOffset: 0,
                suppressScrollX: !1,
                suppressScrollY: !1,
                swipeEasing: !0,
                useBothWheelAxes: !1,
                wheelPropagation: !0,
                wheelSpeed: 1
            }, t) this.settings[a] = t[a];
        this.containerWidth = null, this.containerHeight = null, this.contentWidth = null, this.contentHeight = null;
        var n, o, i = function() {
                return e.classList.add(no.focus)
            },
            s = function() {
                return e.classList.remove(no.focus)
            };
        this.isRtl = "rtl" === Xn(e).direction, !0 === this.isRtl && e.classList.add(ro), this.isNegativeScroll = (o = e.scrollLeft, e.scrollLeft = -1, n = e.scrollLeft < 0, e.scrollLeft = o, n), this.negativeScrollAdjustment = this.isNegativeScroll ? e.scrollWidth - e.clientWidth : 0, this.event = new uo, this.ownerDocument = e.ownerDocument || document, this.scrollbarXRail = Gn(ao.rail("x")), e.appendChild(this.scrollbarXRail), this.scrollbarX = Gn(ao.thumb("x")), this.scrollbarXRail.appendChild(this.scrollbarX), this.scrollbarX.setAttribute("tabindex", 0), this.event.bind(this.scrollbarX, "focus", i), this.event.bind(this.scrollbarX, "blur", s), this.scrollbarXActive = null, this.scrollbarXWidth = null, this.scrollbarXLeft = null;
        var l = Xn(this.scrollbarXRail);
        this.scrollbarXBottom = parseInt(l.bottom, 10), isNaN(this.scrollbarXBottom) ? (this.isScrollbarXUsingBottom = !1, this.scrollbarXTop = fo(l.top)) : this.isScrollbarXUsingBottom = !0, this.railBorderXWidth = fo(l.borderLeftWidth) + fo(l.borderRightWidth), Qn(this.scrollbarXRail, {
            display: "block"
        }), this.railXMarginWidth = fo(l.marginLeft) + fo(l.marginRight), Qn(this.scrollbarXRail, {
            display: ""
        }), this.railXWidth = null, this.railXRatio = null, this.scrollbarYRail = Gn(ao.rail("y")), e.appendChild(this.scrollbarYRail), this.scrollbarY = Gn(ao.thumb("y")), this.scrollbarYRail.appendChild(this.scrollbarY), this.scrollbarY.setAttribute("tabindex", 0), this.event.bind(this.scrollbarY, "focus", i), this.event.bind(this.scrollbarY, "blur", s), this.scrollbarYActive = null, this.scrollbarYHeight = null, this.scrollbarYTop = null;
        var c = Xn(this.scrollbarYRail);
        this.scrollbarYRight = parseInt(c.right, 10), isNaN(this.scrollbarYRight) ? (this.isScrollbarYUsingRight = !1, this.scrollbarYLeft = fo(c.left)) : this.isScrollbarYUsingRight = !0, this.scrollbarYOuterWidth = this.isRtl ? function(e) {
            var t = Xn(e);
            return fo(t.width) + fo(t.paddingLeft) + fo(t.paddingRight) + fo(t.borderLeftWidth) + fo(t.borderRightWidth)
        }(this.scrollbarY) : null, this.railBorderYWidth = fo(c.borderTopWidth) + fo(c.borderBottomWidth), Qn(this.scrollbarYRail, {
            display: "block"
        }), this.railYMarginHeight = fo(c.marginTop) + fo(c.marginBottom), Qn(this.scrollbarYRail, {
            display: ""
        }), this.railYHeight = null, this.railYRatio = null, this.reach = {
            x: e.scrollLeft <= 0 ? "start" : e.scrollLeft >= this.contentWidth - this.containerWidth ? "end" : null,
            y: e.scrollTop <= 0 ? "start" : e.scrollTop >= this.contentHeight - this.containerHeight ? "end" : null
        }, this.isAlive = !0, this.settings.handlers.forEach((function(e) {
            return bo[e](r)
        })), this.lastScrollTop = Math.floor(e.scrollTop), this.lastScrollLeft = e.scrollLeft, this.event.bind(this.element, "scroll", (function(e) {
            return r.onScroll(e)
        })), vo(this)
    };
wo.prototype.update = function() {
    this.isAlive && (this.negativeScrollAdjustment = this.isNegativeScroll ? this.element.scrollWidth - this.element.clientWidth : 0, Qn(this.scrollbarXRail, {
        display: "block"
    }), Qn(this.scrollbarYRail, {
        display: "block"
    }), this.railXMarginWidth = fo(Xn(this.scrollbarXRail).marginLeft) + fo(Xn(this.scrollbarXRail).marginRight), this.railYMarginHeight = fo(Xn(this.scrollbarYRail).marginTop) + fo(Xn(this.scrollbarYRail).marginBottom), Qn(this.scrollbarXRail, {
        display: "none"
    }), Qn(this.scrollbarYRail, {
        display: "none"
    }), vo(this), po(this, "top", 0, !1, !0), po(this, "left", 0, !1, !0), Qn(this.scrollbarXRail, {
        display: ""
    }), Qn(this.scrollbarYRail, {
        display: ""
    }))
}, wo.prototype.onScroll = function(e) {
    this.isAlive && (vo(this), po(this, "top", this.element.scrollTop - this.lastScrollTop), po(this, "left", this.element.scrollLeft - this.lastScrollLeft), this.lastScrollTop = Math.floor(this.element.scrollTop), this.lastScrollLeft = this.element.scrollLeft)
}, wo.prototype.destroy = function() {
    this.isAlive && (this.event.unbindAll(), Zn(this.scrollbarX), Zn(this.scrollbarY), Zn(this.scrollbarXRail), Zn(this.scrollbarYRail), this.removePsClasses(), this.element = null, this.scrollbarX = null, this.scrollbarY = null, this.scrollbarXRail = null, this.scrollbarYRail = null, this.isAlive = !1)
}, wo.prototype.removePsClasses = function() {
    this.element.className = this.element.className.split(" ").filter((function(e) {
        return !e.match(/^ps([-_].+|)$/)
    })).join(" ")
};
const Eo = ["scroll", "ps-scroll-y", "ps-scroll-x", "ps-scroll-up", "ps-scroll-down", "ps-scroll-left", "ps-scroll-right", "ps-y-reach-start", "ps-y-reach-end", "ps-x-reach-start", "ps-x-reach-end"];
var Po = {
        name: "PerfectScrollbar",
        props: {
            options: {
                type: Object,
                required: !1,
                default: () => {}
            },
            tag: {
                type: String,
                required: !1,
                default: "div"
            },
            watchOptions: {
                type: Boolean,
                required: !1,
                default: !1
            }
        },
        emits: Eo,
        data: () => ({
            ps: null
        }),
        watch: {
            watchOptions(e) {
                !e && this.watcher ? this.watcher() : this.createWatcher()
            }
        },
        mounted() {
            this.create(), this.watchOptions && this.createWatcher()
        },
        updated() {
            this.$nextTick((() => {
                this.update()
            }))
        },
        beforeUnmount() {
            this.destroy()
        },
        methods: {
            create() {
                this.ps && this.$isServer || (this.ps = new wo(this.$el, this.options), Eo.forEach((e => {
                    this.ps.element.addEventListener(e, (t => this.$emit(e, t)))
                })))
            },
            createWatcher() {
                this.watcher = this.$watch("options", (() => {
                    this.destroy(), this.create()
                }), {
                    deep: !0
                })
            },
            update() {
                this.ps && this.ps.update()
            },
            destroy() {
                this.ps && (this.ps.destroy(), this.ps = null)
            }
        },
        render() {
            return Za(this.tag, {
                class: "ps"
            }, this.$slots.default && this.$slots.default())
        }
    },
    ko = {
        install: (e, t) => {
            t && (t.name && "string" == typeof t.name && (Po.name = t.name), t.options && "object" == typeof t.options && (Po.props.options.default = () => t.options), t.tag && "string" == typeof t.tag && (Po.props.tag.default = t.tag), t.watchOptions && "boolean" == typeof t.watchOptions && (Po.props.watchOptions = t.watchOptions)), e.component(Po.name, Po)
        }
    };
/*!
 * vue-router v4.0.1
 * (c) 2020 Eduardo San Martin Morote
 * @license MIT
 */
const _o = "function" == typeof Symbol && "symbol" == typeof Symbol.toStringTag,
    So = e => _o ? Symbol(e) : "_vr_" + e,
    Co = So("rvlm"),
    To = So("rvd"),
    xo = So("r"),
    Do = So("rl"),
    Oo = So("rvl"),
    Ro = "undefined" != typeof window;
const Fo = Object.assign;

function $o(e, t) {
    const r = {};
    for (const a in t) {
        const n = t[a];
        r[a] = Array.isArray(n) ? n.map(e) : e(n)
    }
    return r
}
let Ao = () => {};
const Mo = /\/$/;

function Lo(e, t, r = "/") {
    let a, n = {},
        o = "",
        i = "";
    const s = t.indexOf("?"),
        l = t.indexOf("#", s > -1 ? s : 0);
    return s > -1 && (a = t.slice(0, s), o = t.slice(s + 1, l > -1 ? l : t.length), n = e(o)), l > -1 && (a = a || t.slice(0, l), i = t.slice(l, t.length)), a = function(e, t) {
        if (e.startsWith("/")) return e;
        if (!e) return t;
        const r = t.split("/"),
            a = e.split("/");
        let n, o, i = r.length - 1;
        for (n = 0; n < a.length; n++)
            if (o = a[n], 1 !== i && "." !== o) {
                if (".." !== o) break;
                i--
            } return r.slice(0, i).join("/") + "/" + a.slice(n - (n === a.length ? 1 : 0)).join("/")
    }(null != a ? a : t, r), {
        fullPath: a + (o && "?") + o + i,
        path: a,
        query: n,
        hash: i
    }
}

function No(e, t) {
    return !t || e.toLowerCase().indexOf(t.toLowerCase()) ? e : e.slice(t.length) || "/"
}

function Io(e, t) {
    return (e.aliasOf || e) === (t.aliasOf || t)
}

function jo(e, t) {
    if (Object.keys(e).length !== Object.keys(t).length) return !1;
    for (let r in e)
        if (!Uo(e[r], t[r])) return !1;
    return !0
}

function Uo(e, t) {
    return Array.isArray(e) ? Ho(e, t) : Array.isArray(t) ? Ho(t, e) : e === t
}

function Ho(e, t) {
    return Array.isArray(t) ? e.length === t.length && e.every(((e, r) => e === t[r])) : 1 === e.length && e[0] === t
}
var qo, Yo, Bo, Wo;

function Vo(e) {
    if (!e)
        if (Ro) {
            const t = document.querySelector("base");
            e = (e = t && t.getAttribute("href") || "/").replace(/^\w+:\/\/[^\/]+/, "")
        } else e = "/";
    return "/" !== e[0] && "#" !== e[0] && (e = "/" + e), e.replace(Mo, "")
}(Yo = qo || (qo = {})).pop = "pop", Yo.push = "push", (Wo = Bo || (Bo = {})).back = "back", Wo.forward = "forward", Wo.unknown = "";
const zo = /^[^#]+#/;

function Xo(e, t) {
    return e.replace(zo, "#") + t
}
const Qo = () => ({
    left: window.pageXOffset,
    top: window.pageYOffset
});

function Go(e) {
    let t;
    if ("el" in e) {
        let r = e.el;
        const a = "string" == typeof r && r.startsWith("#"),
            n = "string" == typeof r ? a ? document.getElementById(r.slice(1)) : document.querySelector(r) : r;
        if (!n) return;
        t = function(e, t) {
            const r = document.documentElement.getBoundingClientRect(),
                a = e.getBoundingClientRect();
            return {
                behavior: t.behavior,
                left: a.left - r.left - (t.left || 0),
                top: a.top - r.top - (t.top || 0)
            }
        }(n, e)
    } else t = e;
    "scrollBehavior" in document.documentElement.style ? window.scrollTo(t) : window.scrollTo(null != t.left ? t.left : window.pageXOffset, null != t.top ? t.top : window.pageYOffset)
}

function Ko(e, t) {
    return (history.state ? history.state.position - t : -1) + e
}
const Jo = new Map;

function Zo(e, t) {
    const {
        pathname: r,
        search: a,
        hash: n
    } = t;
    if (e.indexOf("#") > -1) {
        let e = n.slice(1);
        return "/" !== e[0] && (e = "/" + e), No(e, "")
    }
    return No(r, e) + a + n
}

function ei(e, t, r, a = !1, n = !1) {
    return {
        back: e,
        current: t,
        forward: r,
        replaced: a,
        position: window.history.length,
        scroll: n ? Qo() : null
    }
}

function ti(e) {
    const {
        history: t,
        location: r
    } = window;
    let a = {
            value: Zo(e, r)
        },
        n = {
            value: t.state
        };

    function o(a, o, i) {
        const s = e.indexOf("#"),
            l = s > -1 ? e.slice(s) + a : location.protocol + "//" + location.host + e + a;
        try {
            t[i ? "replaceState" : "pushState"](o, "", l), n.value = o
        } catch (e) {
            console.error(e), r[i ? "replace" : "assign"](l)
        }
    }
    return n.value || o(a.value, {
        back: null,
        current: a.value,
        forward: null,
        position: t.length - 1,
        replaced: !0,
        scroll: null
    }, !0), {
        location: a,
        state: n,
        push: function(e, r) {
            const i = Fo({}, n.value, t.state, {
                forward: e,
                scroll: Qo()
            });
            o(i.current, i, !0), o(e, Fo({}, ei(a.value, e, null), {
                position: i.position + 1
            }, r), !1), a.value = e
        },
        replace: function(e, r) {
            o(e, Fo({}, t.state, ei(n.value.back, e, n.value.forward, !0), r, {
                position: n.value.position
            }), !0), a.value = e
        }
    }
}

function ri(e) {
    return "string" == typeof e || "symbol" == typeof e
}
const ai = {
        path: "/",
        name: void 0,
        params: {},
        query: {},
        hash: "",
        fullPath: "/",
        matched: [],
        meta: {},
        redirectedFrom: void 0
    },
    ni = So("nf");
var oi, ii;

function si(e, t) {
    return Fo(new Error, {
        type: e,
        [ni]: !0
    }, t)
}

function li(e, t) {
    return e instanceof Error && ni in e && (null == t || !!(e.type & t))
}(ii = oi || (oi = {}))[ii.aborted = 4] = "aborted", ii[ii.cancelled = 8] = "cancelled", ii[ii.duplicated = 16] = "duplicated";
const ci = {
        sensitive: !1,
        strict: !1,
        start: !0,
        end: !0
    },
    ui = /[.+*?^${}()[\]/\\]/g;

function di(e, t) {
    let r = 0;
    for (; r < e.length && r < t.length;) {
        const a = t[r] - e[r];
        if (a) return a;
        r++
    }
    return e.length < t.length ? 1 === e.length && 80 === e[0] ? -1 : 1 : e.length > t.length ? 1 === t.length && 80 === t[0] ? 1 : -1 : 0
}

function hi(e, t) {
    let r = 0;
    const a = e.score,
        n = t.score;
    for (; r < a.length && r < n.length;) {
        const e = di(a[r], n[r]);
        if (e) return e;
        r++
    }
    return n.length - a.length
}
const pi = {
        type: 0,
        value: ""
    },
    fi = /[a-zA-Z0-9_]/;

function mi(e, t, r) {
    const a = function(e, t) {
            const r = Fo({}, ci, t);
            let a = [],
                n = r.start ? "^" : "";
            const o = [];
            for (const t of e) {
                const e = t.length ? [] : [90];
                r.strict && !t.length && (n += "/");
                for (let a = 0; a < t.length; a++) {
                    const i = t[a];
                    let s = 40 + (r.sensitive ? .25 : 0);
                    if (0 === i.type) a || (n += "/"), n += i.value.replace(ui, "\\$&"), s += 40;
                    else if (1 === i.type) {
                        const {
                            value: e,
                            repeatable: t,
                            optional: r,
                            regexp: l
                        } = i;
                        o.push({
                            name: e,
                            repeatable: t,
                            optional: r
                        });
                        const c = l || "[^/]+?";
                        if ("[^/]+?" !== c) {
                            s += 10;
                            try {
                                new RegExp(`(${c})`)
                            } catch (t) {
                                throw new Error(`Invalid custom RegExp for param "${e}" (${c}): ` + t.message)
                            }
                        }
                        let u = t ? `((?:${c})(?:/(?:${c}))*)` : `(${c})`;
                        a || (u = r ? `(?:/${u})` : "/" + u), r && (u += "?"), n += u, s += 20, r && (s += -8), t && (s += -20), ".*" === c && (s += -50)
                    }
                    e.push(s)
                }
                a.push(e)
            }
            if (r.strict && r.end) {
                const e = a.length - 1;
                a[e][a[e].length - 1] += .7000000000000001
            }
            r.strict || (n += "/?"), r.end ? n += "$" : r.strict && (n += "(?:/|$)");
            const i = new RegExp(n, r.sensitive ? "" : "i");
            return {
                re: i,
                score: a,
                keys: o,
                parse: function(e) {
                    const t = e.match(i),
                        r = {};
                    if (!t) return null;
                    for (let e = 1; e < t.length; e++) {
                        const a = t[e] || "",
                            n = o[e - 1];
                        r[n.name] = a && n.repeatable ? a.split("/") : a
                    }
                    return r
                },
                stringify: function(t) {
                    let r = "",
                        a = !1;
                    for (const n of e) {
                        a && r.endsWith("/") || (r += "/"), a = !1;
                        for (const e of n)
                            if (0 === e.type) r += e.value;
                            else if (1 === e.type) {
                            const {
                                value: n,
                                repeatable: o,
                                optional: i
                            } = e, s = n in t ? t[n] : "";
                            if (Array.isArray(s) && !o) throw new Error(`Provided param "${n}" is an array but it is not repeatable (* or + modifiers)`);
                            const l = Array.isArray(s) ? s.join("/") : s;
                            if (!l) {
                                if (!i) throw new Error(`Missing required param "${n}"`);
                                r.endsWith("/") ? r = r.slice(0, -1) : a = !0
                            }
                            r += l
                        }
                    }
                    return r
                }
            }
        }(function(e) {
            if (!e) return [
                []
            ];
            if ("/" === e) return [
                [pi]
            ];
            if (!e.startsWith("/")) throw new Error(`Invalid path "${e}"`);

            function t(e) {
                throw new Error(`ERR (${r})/"${c}": ${e}`)
            }
            let r = 0,
                a = r;
            const n = [];
            let o;

            function i() {
                o && n.push(o), o = []
            }
            let s, l = 0,
                c = "",
                u = "";

            function d() {
                c && (0 === r ? o.push({
                    type: 0,
                    value: c
                }) : 1 === r || 2 === r || 3 === r ? (o.length > 1 && ("*" === s || "+" === s) && t(`A repeatable param (${c}) must be alone in its segment. eg: '/:ids+.`), o.push({
                    type: 1,
                    value: c,
                    regexp: u,
                    repeatable: "*" === s || "+" === s,
                    optional: "*" === s || "?" === s
                })) : t("Invalid state to consume buffer"), c = "")
            }

            function h() {
                c += s
            }
            for (; l < e.length;)
                if (s = e[l++], "\\" !== s || 2 === r) switch (r) {
                    case 0:
                        "/" === s ? (c && d(), i()) : ":" === s ? (d(), r = 1) : h();
                        break;
                    case 4:
                        h(), r = a;
                        break;
                    case 1:
                        "(" === s ? (r = 2, u = "") : fi.test(s) ? h() : (d(), r = 0, "*" !== s && "?" !== s && "+" !== s && l--);
                        break;
                    case 2:
                        ")" === s ? "\\" == u[u.length - 1] ? u = u.slice(0, -1) + s : r = 3 : u += s;
                        break;
                    case 3:
                        d(), r = 0, "*" !== s && "?" !== s && "+" !== s && l--;
                        break;
                    default:
                        t("Unknown state")
                } else a = r, r = 4;
            return 2 === r && t(`Unfinished custom RegExp for param "${c}"`), d(), i(), n
        }(e.path), r),
        n = Fo(a, {
            record: e,
            parent: t,
            children: [],
            alias: []
        });
    return t && !n.record.aliasOf == !t.record.aliasOf && t.children.push(n), n
}

function vi(e, t) {
    const r = [],
        a = new Map;

    function n(e, r, a) {
        let s = !a,
            l = function(e) {
                return {
                    path: e.path,
                    redirect: e.redirect,
                    name: e.name,
                    meta: e.meta || {},
                    aliasOf: void 0,
                    beforeEnter: e.beforeEnter,
                    props: gi(e),
                    children: e.children || [],
                    instances: {},
                    leaveGuards: new Set,
                    updateGuards: new Set,
                    enterCallbacks: {},
                    components: "components" in e ? e.components || {} : {
                        default: e.component
                    }
                }
            }(e);
        l.aliasOf = a && a.record;
        const c = wi(t, e),
            u = [l];
        if ("alias" in e) {
            const t = "string" == typeof e.alias ? [e.alias] : e.alias;
            for (const e of t) u.push(Fo({}, l, {
                components: a ? a.record.components : l.components,
                path: e,
                aliasOf: a ? a.record : l
            }))
        }
        let d, h;
        for (const t of u) {
            let {
                path: u
            } = t;
            if (r && "/" !== u[0]) {
                let e = r.record.path,
                    a = "/" === e[e.length - 1] ? "" : "/";
                t.path = r.record.path + (u && a + u)
            }
            if (d = mi(t, r, c), a ? a.alias.push(d) : (h = h || d, h !== d && h.alias.push(d), s && e.name && !yi(d) && o(e.name)), "children" in l) {
                let e = l.children;
                for (let t = 0; t < e.length; t++) n(e[t], d, a && a.children[t])
            }
            a = a || d, i(d)
        }
        return h ? () => {
            o(h)
        } : Ao
    }

    function o(e) {
        if (ri(e)) {
            const t = a.get(e);
            t && (a.delete(e), r.splice(r.indexOf(t), 1), t.children.forEach(o), t.alias.forEach(o))
        } else {
            let t = r.indexOf(e);
            t > -1 && (r.splice(t, 1), e.record.name && a.delete(e.record.name), e.children.forEach(o), e.alias.forEach(o))
        }
    }

    function i(e) {
        let t = 0;
        for (; t < r.length && hi(e, r[t]) >= 0;) t++;
        r.splice(t, 0, e), e.record.name && !yi(e) && a.set(e.record.name, e)
    }
    return t = wi({
        strict: !1,
        end: !0,
        sensitive: !1
    }, t), e.forEach((e => n(e))), {
        addRoute: n,
        resolve: function(e, t) {
            let n, o, i, s = {};
            if ("name" in e && e.name) {
                if (n = a.get(e.name), !n) throw si(1, {
                    location: e
                });
                i = n.record.name, s = Fo(function(e, t) {
                    let r = {};
                    for (let a of t) a in e && (r[a] = e[a]);
                    return r
                }(t.params, n.keys.filter((e => !e.optional)).map((e => e.name))), e.params), o = n.stringify(s)
            } else if ("path" in e) o = e.path, n = r.find((e => e.re.test(o))), n && (s = n.parse(o), i = n.record.name);
            else {
                if (n = t.name ? a.get(t.name) : r.find((e => e.re.test(t.path))), !n) throw si(1, {
                    location: e,
                    currentLocation: t
                });
                i = n.record.name, s = Fo({}, t.params, e.params), o = n.stringify(s)
            }
            const l = [];
            let c = n;
            for (; c;) l.unshift(c.record), c = c.parent;
            return {
                name: i,
                path: o,
                params: s,
                matched: l,
                meta: bi(l)
            }
        },
        removeRoute: o,
        getRoutes: function() {
            return r
        },
        getRecordMatcher: function(e) {
            return a.get(e)
        }
    }
}

function gi(e) {
    const t = {},
        r = e.props || !1;
    if ("component" in e) t.default = r;
    else
        for (let a in e.components) t[a] = "boolean" == typeof r ? r : r[a];
    return t
}

function yi(e) {
    for (; e;) {
        if (e.record.aliasOf) return !0;
        e = e.parent
    }
    return !1
}

function bi(e) {
    return e.reduce(((e, t) => Fo(e, t.meta)), {})
}

function wi(e, t) {
    let r = {};
    for (let a in e) r[a] = a in t ? t[a] : e[a];
    return r
}
const Ei = /#/g,
    Pi = /&/g,
    ki = /\//g,
    _i = /=/g,
    Si = /\?/g,
    Ci = /\+/g,
    Ti = /%5B/g,
    xi = /%5D/g,
    Di = /%5E/g,
    Oi = /%60/g,
    Ri = /%7B/g,
    Fi = /%7C/g,
    $i = /%7D/g,
    Ai = /%20/g;

function Mi(e) {
    return encodeURI("" + e).replace(Fi, "|").replace(Ti, "[").replace(xi, "]")
}

function Li(e) {
    return Mi(e).replace(Ci, "%2B").replace(Ai, "+").replace(Ei, "%23").replace(Pi, "%26").replace(Oi, "`").replace(Ri, "{").replace($i, "}").replace(Di, "^")
}

function Ni(e) {
    return function(e) {
        return Mi(e).replace(Ei, "%23").replace(Si, "%3F")
    }(e).replace(ki, "%2F")
}

function Ii(e) {
    try {
        return decodeURIComponent("" + e)
    } catch (e) {}
    return "" + e
}

function ji(e) {
    const t = {};
    if ("" === e || "?" === e) return t;
    const r = ("?" === e[0] ? e.slice(1) : e).split("&");
    for (let e = 0; e < r.length; ++e) {
        const a = r[e].replace(Ci, " ");
        let n = a.indexOf("="),
            o = Ii(n < 0 ? a : a.slice(0, n)),
            i = n < 0 ? null : Ii(a.slice(n + 1));
        if (o in t) {
            let e = t[o];
            Array.isArray(e) || (e = t[o] = [e]), e.push(i)
        } else t[o] = i
    }
    return t
}

function Ui(e) {
    let t = "";
    for (let r in e) {
        t.length && (t += "&");
        const a = e[r];
        if (r = Li(r).replace(_i, "%3D"), null == a) {
            void 0 !== a && (t += r);
            continue
        }
        let n = Array.isArray(a) ? a.map((e => e && Li(e))) : [a && Li(a)];
        for (let e = 0; e < n.length; e++) t += (e ? "&" : "") + r, null != n[e] && (t += "=" + n[e])
    }
    return t
}

function Hi(e) {
    const t = {};
    for (let r in e) {
        let a = e[r];
        void 0 !== a && (t[r] = Array.isArray(a) ? a.map((e => null == e ? null : "" + e)) : null == a ? a : "" + a)
    }
    return t
}

function qi() {
    let e = [];
    return {
        add: function(t) {
            return e.push(t), () => {
                const r = e.indexOf(t);
                r > -1 && e.splice(r, 1)
            }
        },
        list: () => e,
        reset: function() {
            e = []
        }
    }
}

function Yi(e, t, r, a, n) {
    const o = a && (a.enterCallbacks[n] = a.enterCallbacks[n] || []);
    return () => new Promise(((i, s) => {
        const l = e => {
                var l;
                !1 === e ? s(si(4, {
                    from: r,
                    to: t
                })) : e instanceof Error ? s(e) : "string" == typeof(l = e) || l && "object" == typeof l ? s(si(2, {
                    from: t,
                    to: e
                })) : (o && a.enterCallbacks[n] === o && "function" == typeof e && o.push(e), i())
            },
            c = e.call(a && a.instances[n], t, r, l);
        let u = Promise.resolve(c);
        e.length < 3 && (u = u.then(l)), u.catch((e => s(e)))
    }))
}

function Bi(e, t, r, a) {
    const n = [];
    for (const i of e)
        for (const e in i.components) {
            let s = i.components[e];
            if ("beforeRouteEnter" === t || i.instances[e])
                if ("object" == typeof(o = s) || "displayName" in o || "props" in o || "__vccOpts" in o) {
                    const o = (s.__vccOpts || s)[t];
                    o && n.push(Yi(o, r, a, i, e))
                } else {
                    let o = s();
                    o = o.catch(console.error), n.push((() => o.then((n => {
                        if (!n) return Promise.reject(new Error(`Couldn't resolve component "${e}" at "${i.path}"`));
                        const o = (s = n).__esModule || _o && "Module" === s[Symbol.toStringTag] ? n.default : n;
                        var s;
                        i.components[e] = o;
                        const l = o[t];
                        return l && Yi(l, r, a, i, e)()
                    }))))
                }
        }
    var o;
    return n
}

function Wi(e) {
    const t = Da(xo),
        r = Da(Do),
        a = Ja((() => t.resolve(rt(e.to)))),
        n = Ja((() => {
            let {
                matched: e
            } = a.value, {
                length: t
            } = e;
            const n = e[t - 1];
            let o = r.matched;
            if (!n || !o.length) return -1;
            let i = o.findIndex(Io.bind(null, n));
            if (i > -1) return i;
            let s = zi(e[t - 2]);
            return t > 1 && zi(n) === s && o[o.length - 1].path !== s ? o.findIndex(Io.bind(null, e[t - 2])) : i
        })),
        o = Ja((() => n.value > -1 && function(e, t) {
            for (let r in t) {
                let a = t[r],
                    n = e[r];
                if ("string" == typeof a) {
                    if (a !== n) return !1
                } else if (!Array.isArray(n) || n.length !== a.length || a.some(((e, t) => e !== n[t]))) return !1
            }
            return !0
        }(r.params, a.value.params))),
        i = Ja((() => n.value > -1 && n.value === r.matched.length - 1 && jo(r.params, a.value.params)));
    return {
        route: a,
        href: Ja((() => a.value.href)),
        isActive: o,
        isExactActive: i,
        navigate: function(r = {}) {
            return function(e) {
                if (e.metaKey || e.altKey || e.ctrlKey || e.shiftKey) return;
                if (e.defaultPrevented) return;
                if (void 0 !== e.button && 0 !== e.button) return;
                if (e.currentTarget && e.currentTarget.getAttribute) {
                    const t = e.currentTarget.getAttribute("target");
                    if (/\b_blank\b/i.test(t)) return
                }
                e.preventDefault && e.preventDefault();
                return !0
            }(r) ? t[rt(e.replace) ? "replace" : "push"](rt(e.to)) : Promise.resolve()
        }
    }
}
const Vi = Yr({
    name: "RouterLink",
    props: {
        to: {
            type: [String, Object],
            required: !0
        },
        activeClass: String,
        exactActiveClass: String,
        custom: Boolean,
        ariaCurrentValue: {
            type: String,
            default: "page"
        }
    },
    setup(e, {
        slots: t,
        attrs: r
    }) {
        const a = Be(Wi(e)),
            {
                options: n
            } = Da(xo),
            o = Ja((() => ({
                [Xi(e.activeClass, n.linkActiveClass, "router-link-active")]: a.isActive,
                [Xi(e.exactActiveClass, n.linkExactActiveClass, "router-link-exact-active")]: a.isExactActive
            })));
        return () => {
            const n = t.default && t.default(a);
            return e.custom ? n : Za("a", Fo({
                "aria-current": a.isExactActive ? e.ariaCurrentValue : null,
                onClick: a.navigate,
                href: a.href
            }, r, {
                class: o.value
            }), n)
        }
    }
});

function zi(e) {
    return e ? e.aliasOf ? e.aliasOf.path : e.path : ""
}
const Xi = (e, t, r) => null != e ? e : null != t ? t : r;

function Qi(e, t) {
    if (!e) return null;
    const r = e(t);
    return 1 === r.length ? r[0] : r
}
const Gi = Yr({
    name: "RouterView",
    props: {
        name: {
            type: String,
            default: "default"
        },
        route: Object
    },
    setup(e, {
        attrs: t,
        slots: r
    }) {
        const a = Da(Oo),
            n = Ja((() => e.route || a.value)),
            o = Da(To, 0),
            i = Ja((() => n.value.matched[o]));
        xa(To, o + 1), xa(Co, i), xa(Oo, n);
        const s = Ze();
        return yr((() => [s.value, i.value, e.name]), (([e, t, r], [a, n, o]) => {
            t && (t.instances[r] = e, n && n !== t && e && e === a && (t.leaveGuards = n.leaveGuards, t.updateGuards = n.updateGuards)), !e || !t || n && Io(t, n) && a || (t.enterCallbacks[r] || []).forEach((t => t(e)))
        }), {
            flush: "post"
        }), () => {
            const a = n.value,
                o = i.value,
                l = o && o.components[e.name],
                c = e.name;
            if (!l) return Qi(r.default, {
                Component: l,
                route: a
            });
            const u = o.props[e.name],
                d = u ? !0 === u ? a.params : "function" == typeof u ? u(a) : u : null,
                h = Za(l, Fo({}, d, t, {
                    onVnodeUnmounted: e => {
                        e.component.isUnmounted && (o.instances[c] = null)
                    },
                    ref: s
                }));
            return Qi(r.default, {
                Component: h,
                route: a
            }) || h
        }
    }
});
var Ki = "undefined" != typeof globalThis ? globalThis : "undefined" != typeof window ? window : "undefined" != typeof global ? global : "undefined" != typeof self ? self : {};

function Ji(e, t, r) {
    return e(r = {
        path: t,
        exports: {},
        require: function(e, t) {
            return function() {
                throw new Error("Dynamic requires are not currently supported by @rollup/plugin-commonjs")
            }(null == t && r.path)
        }
    }, r.exports), r.exports
}
var Zi = Ji((function(e, t) {
        Object.defineProperty(t, "__esModule", {
            value: !0
        }), t.hook = t.target = t.isBrowser = void 0, t.isBrowser = "undefined" != typeof navigator, t.target = t.isBrowser ? window : void 0 !== Ki ? Ki : {}, t.hook = t.target.__VUE_DEVTOOLS_GLOBAL_HOOK__
    })),
    es = Ji((function(e, t) {
        Object.defineProperty(t, "__esModule", {
            value: !0
        }), t.ApiHookEvents = void 0, (t.ApiHookEvents || (t.ApiHookEvents = {})).SETUP_DEVTOOLS_PLUGIN = "devtools-plugin:setup"
    })),
    ts = Ji((function(e, t) {
        Object.defineProperty(t, "__esModule", {
            value: !0
        })
    })),
    rs = Ji((function(e, t) {
        Object.defineProperty(t, "__esModule", {
            value: !0
        })
    })),
    as = Ji((function(e, t) {
        Object.defineProperty(t, "__esModule", {
            value: !0
        })
    })),
    ns = Ji((function(e, t) {
        Object.defineProperty(t, "__esModule", {
            value: !0
        })
    })),
    os = Ji((function(e, t) {
        var r;
        Object.defineProperty(t, "__esModule", {
            value: !0
        }), t.Hooks = void 0, (r = t.Hooks || (t.Hooks = {})).TRANSFORM_CALL = "transformCall", r.GET_APP_RECORD_NAME = "getAppRecordName", r.GET_APP_ROOT_INSTANCE = "getAppRootInstance", r.REGISTER_APPLICATION = "registerApplication", r.WALK_COMPONENT_TREE = "walkComponentTree", r.WALK_COMPONENT_PARENTS = "walkComponentParents", r.INSPECT_COMPONENT = "inspectComponent", r.GET_COMPONENT_BOUNDS = "getComponentBounds", r.GET_COMPONENT_NAME = "getComponentName", r.GET_ELEMENT_COMPONENT = "getElementComponent", r.GET_INSPECTOR_TREE = "getInspectorTree", r.GET_INSPECTOR_STATE = "getInspectorState"
    })),
    is = Ji((function(e, t) {
        var r = Ki && Ki.__createBinding || (Object.create ? function(e, t, r, a) {
                void 0 === a && (a = r), Object.defineProperty(e, a, {
                    enumerable: !0,
                    get: function() {
                        return t[r]
                    }
                })
            } : function(e, t, r, a) {
                void 0 === a && (a = r), e[a] = t[r]
            }),
            a = Ki && Ki.__exportStar || function(e, t) {
                for (var a in e) "default" === a || t.hasOwnProperty(a) || r(t, e, a)
            };
        Object.defineProperty(t, "__esModule", {
            value: !0
        }), a(ts, t), a(rs, t), a(as, t), a(ns, t), a(os, t)
    }));
Ji((function(e, t) {
    var r = Ki && Ki.__createBinding || (Object.create ? function(e, t, r, a) {
            void 0 === a && (a = r), Object.defineProperty(e, a, {
                enumerable: !0,
                get: function() {
                    return t[r]
                }
            })
        } : function(e, t, r, a) {
            void 0 === a && (a = r), e[a] = t[r]
        }),
        a = Ki && Ki.__exportStar || function(e, t) {
            for (var a in e) "default" === a || t.hasOwnProperty(a) || r(t, e, a)
        };
    Object.defineProperty(t, "__esModule", {
        value: !0
    }), t.setupDevtoolsPlugin = void 0, a(is, t), t.setupDevtoolsPlugin = function(e, t) {
        if (Zi.hook) Zi.hook.emit(es.ApiHookEvents.SETUP_DEVTOOLS_PLUGIN, e, t);
        else {
            (Zi.target.__VUE_DEVTOOLS_PLUGINS__ = Zi.target.__VUE_DEVTOOLS_PLUGINS__ || []).push({
                pluginDescriptor: e,
                setupFn: t
            })
        }
    }
}));

function ss(e) {
    return e.reduce(((e, t) => e.then((() => t()))), Promise.resolve())
}
const ls = (e, t = ".") => e.filter((e => e)).join(t),
    cs = e => Object.entries(e).map((([e, t]) => [e, t && "object" == typeof t ? cs(t) : t])).reduce(((e, [t, r]) => (null == r || (e[t] = r), e)), {});
"undefined" != typeof globalThis ? globalThis : "undefined" != typeof window ? window : "undefined" != typeof global ? global : "undefined" != typeof self && self;

function us(e, t, r) {
    return e(r = {
        path: t,
        exports: {},
        require: function(e, t) {
            return function() {
                throw new Error("Dynamic requires are not currently supported by @rollup/plugin-commonjs")
            }(null == t && r.path)
        }
    }, r.exports), r.exports
}
var ds = us((function(e, t) {
        /** @license URI.js v4.4.0 (c) 2011 Gary Court. License: http://github.com/garycourt/uri-js */
        ! function(e) {
            function t() {
                for (var e = arguments.length, t = Array(e), r = 0; r < e; r++) t[r] = arguments[r];
                if (t.length > 1) {
                    t[0] = t[0].slice(0, -1);
                    for (var a = t.length - 1, n = 1; n < a; ++n) t[n] = t[n].slice(1, -1);
                    return t[a] = t[a].slice(1), t.join("")
                }
                return t[0]
            }

            function r(e) {
                return "(?:" + e + ")"
            }

            function a(e) {
                return void 0 === e ? "undefined" : null === e ? "null" : Object.prototype.toString.call(e).split(" ").pop().split("]").shift().toLowerCase()
            }

            function n(e) {
                return e.toUpperCase()
            }

            function o(e) {
                return null != e ? e instanceof Array ? e : "number" != typeof e.length || e.split || e.setInterval || e.call ? [e] : Array.prototype.slice.call(e) : []
            }

            function i(e, t) {
                var r = e;
                if (t)
                    for (var a in t) r[a] = t[a];
                return r
            }

            function s(e) {
                var a = "[A-Za-z]",
                    n = "[0-9]",
                    o = t(n, "[A-Fa-f]"),
                    i = r(r("%[EFef]" + o + "%" + o + o + "%" + o + o) + "|" + r("%[89A-Fa-f]" + o + "%" + o + o) + "|" + r("%" + o + o)),
                    s = "[\\!\\$\\&\\'\\(\\)\\*\\+\\,\\;\\=]",
                    l = t("[\\:\\/\\?\\#\\[\\]\\@]", s),
                    c = e ? "[\\uE000-\\uF8FF]" : "[]",
                    u = t(a, n, "[\\-\\.\\_\\~]", e ? "[\\xA0-\\u200D\\u2010-\\u2029\\u202F-\\uD7FF\\uF900-\\uFDCF\\uFDF0-\\uFFEF]" : "[]"),
                    d = (r(a + t(a, n, "[\\+\\-\\.]") + "*"), r(r(i + "|" + t(u, s, "[\\:]")) + "*"), r(r("25[0-5]") + "|" + r("2[0-4]" + n) + "|" + r("1" + n + n) + "|" + r("0?[1-9]" + n) + "|0?0?" + n)),
                    h = r(d + "\\." + d + "\\." + d + "\\." + d),
                    p = r(o + "{1,4}"),
                    f = r(r(p + "\\:" + p) + "|" + h),
                    m = r(r(p + "\\:") + "{6}" + f),
                    v = r("\\:\\:" + r(p + "\\:") + "{5}" + f),
                    g = r(r(p) + "?\\:\\:" + r(p + "\\:") + "{4}" + f),
                    y = r(r(r(p + "\\:") + "{0,1}" + p) + "?\\:\\:" + r(p + "\\:") + "{3}" + f),
                    b = r(r(r(p + "\\:") + "{0,2}" + p) + "?\\:\\:" + r(p + "\\:") + "{2}" + f),
                    w = r(r(r(p + "\\:") + "{0,3}" + p) + "?\\:\\:" + p + "\\:" + f),
                    E = r(r(r(p + "\\:") + "{0,4}" + p) + "?\\:\\:" + f),
                    P = r(r(r(p + "\\:") + "{0,5}" + p) + "?\\:\\:" + p),
                    k = r(r(r(p + "\\:") + "{0,6}" + p) + "?\\:\\:"),
                    _ = r([m, v, g, y, b, w, E, P, k].join("|")),
                    S = r(r(u + "|" + i) + "+"),
                    C = (r("[vV]" + o + "+\\." + t(u, s, "[\\:]") + "+"), r(r(i + "|" + t(u, s)) + "*"), r(i + "|" + t(u, s, "[\\:\\@]")));
                return r(r(i + "|" + t(u, s, "[\\@]")) + "+"), r(r(C + "|" + t("[\\/\\?]", c)) + "*"), {
                    NOT_SCHEME: new RegExp(t("[^]", a, n, "[\\+\\-\\.]"), "g"),
                    NOT_USERINFO: new RegExp(t("[^\\%\\:]", u, s), "g"),
                    NOT_HOST: new RegExp(t("[^\\%\\[\\]\\:]", u, s), "g"),
                    NOT_PATH: new RegExp(t("[^\\%\\/\\:\\@]", u, s), "g"),
                    NOT_PATH_NOSCHEME: new RegExp(t("[^\\%\\/\\@]", u, s), "g"),
                    NOT_QUERY: new RegExp(t("[^\\%]", u, s, "[\\:\\@\\/\\?]", c), "g"),
                    NOT_FRAGMENT: new RegExp(t("[^\\%]", u, s, "[\\:\\@\\/\\?]"), "g"),
                    ESCAPE: new RegExp(t("[^]", u, s), "g"),
                    UNRESERVED: new RegExp(u, "g"),
                    OTHER_CHARS: new RegExp(t("[^\\%]", u, l), "g"),
                    PCT_ENCODED: new RegExp(i, "g"),
                    IPV4ADDRESS: new RegExp("^(" + h + ")$"),
                    IPV6ADDRESS: new RegExp("^\\[?(" + _ + ")" + r(r("\\%25|\\%(?!" + o + "{2})") + "(" + S + ")") + "?\\]?$")
                }
            }
            var l = s(!1),
                c = s(!0),
                u = function() {
                    function e(e, t) {
                        var r = [],
                            a = !0,
                            n = !1,
                            o = void 0;
                        try {
                            for (var i, s = e[Symbol.iterator](); !(a = (i = s.next()).done) && (r.push(i.value), !t || r.length !== t); a = !0);
                        } catch (e) {
                            n = !0, o = e
                        } finally {
                            try {
                                !a && s.return && s.return()
                            } finally {
                                if (n) throw o
                            }
                        }
                        return r
                    }
                    return function(t, r) {
                        if (Array.isArray(t)) return t;
                        if (Symbol.iterator in Object(t)) return e(t, r);
                        throw new TypeError("Invalid attempt to destructure non-iterable instance")
                    }
                }(),
                d = function(e) {
                    if (Array.isArray(e)) {
                        for (var t = 0, r = Array(e.length); t < e.length; t++) r[t] = e[t];
                        return r
                    }
                    return Array.from(e)
                },
                h = 2147483647,
                p = 36,
                f = 1,
                m = 26,
                v = 38,
                g = 700,
                y = 72,
                b = 128,
                w = "-",
                E = /^xn--/,
                P = /[^\0-\x7E]/,
                k = /[\x2E\u3002\uFF0E\uFF61]/g,
                _ = {
                    overflow: "Overflow: input needs wider integers to process",
                    "not-basic": "Illegal input >= 0x80 (not a basic code point)",
                    "invalid-input": "Invalid input"
                },
                S = p - f,
                C = Math.floor,
                T = String.fromCharCode;

            function x(e) {
                throw new RangeError(_[e])
            }

            function D(e, t) {
                for (var r = [], a = e.length; a--;) r[a] = t(e[a]);
                return r
            }

            function O(e, t) {
                var r = e.split("@"),
                    a = "";
                return r.length > 1 && (a = r[0] + "@", e = r[1]), a + D((e = e.replace(k, ".")).split("."), t).join(".")
            }

            function R(e) {
                for (var t = [], r = 0, a = e.length; r < a;) {
                    var n = e.charCodeAt(r++);
                    if (n >= 55296 && n <= 56319 && r < a) {
                        var o = e.charCodeAt(r++);
                        56320 == (64512 & o) ? t.push(((1023 & n) << 10) + (1023 & o) + 65536) : (t.push(n), r--)
                    } else t.push(n)
                }
                return t
            }
            var F = function(e) {
                    return e - 48 < 10 ? e - 22 : e - 65 < 26 ? e - 65 : e - 97 < 26 ? e - 97 : p
                },
                $ = function(e, t) {
                    return e + 22 + 75 * (e < 26) - ((0 != t) << 5)
                },
                A = function(e, t, r) {
                    var a = 0;
                    for (e = r ? C(e / g) : e >> 1, e += C(e / t); e > S * m >> 1; a += p) e = C(e / S);
                    return C(a + (S + 1) * e / (e + v))
                },
                M = function(e) {
                    var t = [],
                        r = e.length,
                        a = 0,
                        n = b,
                        o = y,
                        i = e.lastIndexOf(w);
                    i < 0 && (i = 0);
                    for (var s = 0; s < i; ++s) e.charCodeAt(s) >= 128 && x("not-basic"), t.push(e.charCodeAt(s));
                    for (var l = i > 0 ? i + 1 : 0; l < r;) {
                        for (var c = a, u = 1, d = p;; d += p) {
                            l >= r && x("invalid-input");
                            var v = F(e.charCodeAt(l++));
                            (v >= p || v > C((h - a) / u)) && x("overflow"), a += v * u;
                            var g = d <= o ? f : d >= o + m ? m : d - o;
                            if (v < g) break;
                            var E = p - g;
                            u > C(h / E) && x("overflow"), u *= E
                        }
                        var P = t.length + 1;
                        o = A(a - c, P, 0 == c), C(a / P) > h - n && x("overflow"), n += C(a / P), a %= P, t.splice(a++, 0, n)
                    }
                    return String.fromCodePoint.apply(String, t)
                },
                L = function(e) {
                    var t = [],
                        r = (e = R(e)).length,
                        a = b,
                        n = 0,
                        o = y,
                        i = !0,
                        s = !1,
                        l = void 0;
                    try {
                        for (var c, u = e[Symbol.iterator](); !(i = (c = u.next()).done); i = !0) {
                            var d = c.value;
                            d < 128 && t.push(T(d))
                        }
                    } catch (e) {
                        s = !0, l = e
                    } finally {
                        try {
                            !i && u.return && u.return()
                        } finally {
                            if (s) throw l
                        }
                    }
                    var v = t.length,
                        g = v;
                    for (v && t.push(w); g < r;) {
                        var E = h,
                            P = !0,
                            k = !1,
                            _ = void 0;
                        try {
                            for (var S, D = e[Symbol.iterator](); !(P = (S = D.next()).done); P = !0) {
                                var O = S.value;
                                O >= a && O < E && (E = O)
                            }
                        } catch (e) {
                            k = !0, _ = e
                        } finally {
                            try {
                                !P && D.return && D.return()
                            } finally {
                                if (k) throw _
                            }
                        }
                        var F = g + 1;
                        E - a > C((h - n) / F) && x("overflow"), n += (E - a) * F, a = E;
                        var M = !0,
                            L = !1,
                            N = void 0;
                        try {
                            for (var I, j = e[Symbol.iterator](); !(M = (I = j.next()).done); M = !0) {
                                var U = I.value;
                                if (U < a && ++n > h && x("overflow"), U == a) {
                                    for (var H = n, q = p;; q += p) {
                                        var Y = q <= o ? f : q >= o + m ? m : q - o;
                                        if (H < Y) break;
                                        var B = H - Y,
                                            W = p - Y;
                                        t.push(T($(Y + B % W, 0))), H = C(B / W)
                                    }
                                    t.push(T($(H, 0))), o = A(n, F, g == v), n = 0, ++g
                                }
                            }
                        } catch (e) {
                            L = !0, N = e
                        } finally {
                            try {
                                !M && j.return && j.return()
                            } finally {
                                if (L) throw N
                            }
                        }++n, ++a
                    }
                    return t.join("")
                },
                N = function(e) {
                    return O(e, (function(e) {
                        return E.test(e) ? M(e.slice(4).toLowerCase()) : e
                    }))
                },
                I = function(e) {
                    return O(e, (function(e) {
                        return P.test(e) ? "xn--" + L(e) : e
                    }))
                },
                j = {
                    version: "2.1.0",
                    ucs2: {
                        decode: R,
                        encode: function(e) {
                            return String.fromCodePoint.apply(String, d(e))
                        }
                    },
                    decode: M,
                    encode: L,
                    toASCII: I,
                    toUnicode: N
                },
                U = {};

            function H(e) {
                var t = e.charCodeAt(0);
                return t < 16 ? "%0" + t.toString(16).toUpperCase() : t < 128 ? "%" + t.toString(16).toUpperCase() : t < 2048 ? "%" + (t >> 6 | 192).toString(16).toUpperCase() + "%" + (63 & t | 128).toString(16).toUpperCase() : "%" + (t >> 12 | 224).toString(16).toUpperCase() + "%" + (t >> 6 & 63 | 128).toString(16).toUpperCase() + "%" + (63 & t | 128).toString(16).toUpperCase()
            }

            function q(e) {
                for (var t = "", r = 0, a = e.length; r < a;) {
                    var n = parseInt(e.substr(r + 1, 2), 16);
                    if (n < 128) t += String.fromCharCode(n), r += 3;
                    else if (n >= 194 && n < 224) {
                        if (a - r >= 6) {
                            var o = parseInt(e.substr(r + 4, 2), 16);
                            t += String.fromCharCode((31 & n) << 6 | 63 & o)
                        } else t += e.substr(r, 6);
                        r += 6
                    } else if (n >= 224) {
                        if (a - r >= 9) {
                            var i = parseInt(e.substr(r + 4, 2), 16),
                                s = parseInt(e.substr(r + 7, 2), 16);
                            t += String.fromCharCode((15 & n) << 12 | (63 & i) << 6 | 63 & s)
                        } else t += e.substr(r, 9);
                        r += 9
                    } else t += e.substr(r, 3), r += 3
                }
                return t
            }

            function Y(e, t) {
                function r(e) {
                    var r = q(e);
                    return r.match(t.UNRESERVED) ? r : e
                }
                return e.scheme && (e.scheme = String(e.scheme).replace(t.PCT_ENCODED, r).toLowerCase().replace(t.NOT_SCHEME, "")), void 0 !== e.userinfo && (e.userinfo = String(e.userinfo).replace(t.PCT_ENCODED, r).replace(t.NOT_USERINFO, H).replace(t.PCT_ENCODED, n)), void 0 !== e.host && (e.host = String(e.host).replace(t.PCT_ENCODED, r).toLowerCase().replace(t.NOT_HOST, H).replace(t.PCT_ENCODED, n)), void 0 !== e.path && (e.path = String(e.path).replace(t.PCT_ENCODED, r).replace(e.scheme ? t.NOT_PATH : t.NOT_PATH_NOSCHEME, H).replace(t.PCT_ENCODED, n)), void 0 !== e.query && (e.query = String(e.query).replace(t.PCT_ENCODED, r).replace(t.NOT_QUERY, H).replace(t.PCT_ENCODED, n)), void 0 !== e.fragment && (e.fragment = String(e.fragment).replace(t.PCT_ENCODED, r).replace(t.NOT_FRAGMENT, H).replace(t.PCT_ENCODED, n)), e
            }

            function B(e) {
                return e.replace(/^0*(.*)/, "$1") || "0"
            }

            function W(e, t) {
                var r = e.match(t.IPV4ADDRESS) || [],
                    a = u(r, 2)[1];
                return a ? a.split(".").map(B).join(".") : e
            }

            function V(e, t) {
                var r = e.match(t.IPV6ADDRESS) || [],
                    a = u(r, 3),
                    n = a[1],
                    o = a[2];
                if (n) {
                    for (var i = n.toLowerCase().split("::").reverse(), s = u(i, 2), l = s[0], c = s[1], d = c ? c.split(":").map(B) : [], h = l.split(":").map(B), p = t.IPV4ADDRESS.test(h[h.length - 1]), f = p ? 7 : 8, m = h.length - f, v = Array(f), g = 0; g < f; ++g) v[g] = d[g] || h[m + g] || "";
                    p && (v[f - 1] = W(v[f - 1], t));
                    var y = v.reduce((function(e, t, r) {
                            if (!t || "0" === t) {
                                var a = e[e.length - 1];
                                a && a.index + a.length === r ? a.length++ : e.push({
                                    index: r,
                                    length: 1
                                })
                            }
                            return e
                        }), []).sort((function(e, t) {
                            return t.length - e.length
                        }))[0],
                        b = void 0;
                    if (y && y.length > 1) {
                        var w = v.slice(0, y.index),
                            E = v.slice(y.index + y.length);
                        b = w.join(":") + "::" + E.join(":")
                    } else b = v.join(":");
                    return o && (b += "%" + o), b
                }
                return e
            }
            var z = /^(?:([^:\/?#]+):)?(?:\/\/((?:([^\/?#@]*)@)?(\[[^\/?#\]]+\]|[^\/?#:]*)(?:\:(\d*))?))?([^?#]*)(?:\?([^#]*))?(?:#((?:.|\n|\r)*))?/i,
                X = void 0 === "".match(/(){0}/)[1];

            function Q(e) {
                var t = arguments.length > 1 && void 0 !== arguments[1] ? arguments[1] : {},
                    r = {},
                    a = !1 !== t.iri ? c : l;
                "suffix" === t.reference && (e = (t.scheme ? t.scheme + ":" : "") + "//" + e);
                var n = e.match(z);
                if (n) {
                    X ? (r.scheme = n[1], r.userinfo = n[3], r.host = n[4], r.port = parseInt(n[5], 10), r.path = n[6] || "", r.query = n[7], r.fragment = n[8], isNaN(r.port) && (r.port = n[5])) : (r.scheme = n[1] || void 0, r.userinfo = -1 !== e.indexOf("@") ? n[3] : void 0, r.host = -1 !== e.indexOf("//") ? n[4] : void 0, r.port = parseInt(n[5], 10), r.path = n[6] || "", r.query = -1 !== e.indexOf("?") ? n[7] : void 0, r.fragment = -1 !== e.indexOf("#") ? n[8] : void 0, isNaN(r.port) && (r.port = e.match(/\/\/(?:.|\n)*\:(?:\/|\?|\#|$)/) ? n[4] : void 0)), r.host && (r.host = V(W(r.host, a), a)), void 0 !== r.scheme || void 0 !== r.userinfo || void 0 !== r.host || void 0 !== r.port || r.path || void 0 !== r.query ? void 0 === r.scheme ? r.reference = "relative" : void 0 === r.fragment ? r.reference = "absolute" : r.reference = "uri" : r.reference = "same-document", t.reference && "suffix" !== t.reference && t.reference !== r.reference && (r.error = r.error || "URI is not a " + t.reference + " reference.");
                    var o = U[(t.scheme || r.scheme || "").toLowerCase()];
                    if (t.unicodeSupport || o && o.unicodeSupport) Y(r, a);
                    else {
                        if (r.host && (t.domainHost || o && o.domainHost)) try {
                            r.host = j.toASCII(r.host.replace(a.PCT_ENCODED, q).toLowerCase())
                        } catch (e) {
                            r.error = r.error || "Host's domain name can not be converted to ASCII via punycode: " + e
                        }
                        Y(r, l)
                    }
                    o && o.parse && o.parse(r, t)
                } else r.error = r.error || "URI can not be parsed.";
                return r
            }

            function G(e, t) {
                var r = !1 !== t.iri ? c : l,
                    a = [];
                return void 0 !== e.userinfo && (a.push(e.userinfo), a.push("@")), void 0 !== e.host && a.push(V(W(String(e.host), r), r).replace(r.IPV6ADDRESS, (function(e, t, r) {
                    return "[" + t + (r ? "%25" + r : "") + "]"
                }))), "number" != typeof e.port && "string" != typeof e.port || (a.push(":"), a.push(String(e.port))), a.length ? a.join("") : void 0
            }
            var K = /^\.\.?\//,
                J = /^\/\.(\/|$)/,
                Z = /^\/\.\.(\/|$)/,
                ee = /^\/?(?:.|\n)*?(?=\/|$)/;

            function te(e) {
                for (var t = []; e.length;)
                    if (e.match(K)) e = e.replace(K, "");
                    else if (e.match(J)) e = e.replace(J, "/");
                else if (e.match(Z)) e = e.replace(Z, "/"), t.pop();
                else if ("." === e || ".." === e) e = "";
                else {
                    var r = e.match(ee);
                    if (!r) throw new Error("Unexpected dot segment condition");
                    var a = r[0];
                    e = e.slice(a.length), t.push(a)
                }
                return t.join("")
            }

            function re(e) {
                var t = arguments.length > 1 && void 0 !== arguments[1] ? arguments[1] : {},
                    r = t.iri ? c : l,
                    a = [],
                    n = U[(t.scheme || e.scheme || "").toLowerCase()];
                if (n && n.serialize && n.serialize(e, t), e.host)
                    if (r.IPV6ADDRESS.test(e.host));
                    else if (t.domainHost || n && n.domainHost) try {
                    e.host = t.iri ? j.toUnicode(e.host) : j.toASCII(e.host.replace(r.PCT_ENCODED, q).toLowerCase())
                } catch (r) {
                    e.error = e.error || "Host's domain name can not be converted to " + (t.iri ? "Unicode" : "ASCII") + " via punycode: " + r
                }
                Y(e, r), "suffix" !== t.reference && e.scheme && (a.push(e.scheme), a.push(":"));
                var o = G(e, t);
                if (void 0 !== o && ("suffix" !== t.reference && a.push("//"), a.push(o), e.path && "/" !== e.path.charAt(0) && a.push("/")), void 0 !== e.path) {
                    var i = e.path;
                    t.absolutePath || n && n.absolutePath || (i = te(i)), void 0 === o && (i = i.replace(/^\/\//, "/%2F")), a.push(i)
                }
                return void 0 !== e.query && (a.push("?"), a.push(e.query)), void 0 !== e.fragment && (a.push("#"), a.push(e.fragment)), a.join("")
            }

            function ae(e, t) {
                var r = arguments.length > 2 && void 0 !== arguments[2] ? arguments[2] : {},
                    a = {};
                return arguments[3] || (e = Q(re(e, r), r), t = Q(re(t, r), r)), !(r = r || {}).tolerant && t.scheme ? (a.scheme = t.scheme, a.userinfo = t.userinfo, a.host = t.host, a.port = t.port, a.path = te(t.path || ""), a.query = t.query) : (void 0 !== t.userinfo || void 0 !== t.host || void 0 !== t.port ? (a.userinfo = t.userinfo, a.host = t.host, a.port = t.port, a.path = te(t.path || ""), a.query = t.query) : (t.path ? ("/" === t.path.charAt(0) ? a.path = te(t.path) : (void 0 === e.userinfo && void 0 === e.host && void 0 === e.port || e.path ? e.path ? a.path = e.path.slice(0, e.path.lastIndexOf("/") + 1) + t.path : a.path = t.path : a.path = "/" + t.path, a.path = te(a.path)), a.query = t.query) : (a.path = e.path, void 0 !== t.query ? a.query = t.query : a.query = e.query), a.userinfo = e.userinfo, a.host = e.host, a.port = e.port), a.scheme = e.scheme), a.fragment = t.fragment, a
            }

            function ne(e, t, r) {
                var a = i({
                    scheme: "null"
                }, r);
                return re(ae(Q(e, a), Q(t, a), a, !0), a)
            }

            function oe(e, t) {
                return "string" == typeof e ? e = re(Q(e, t), t) : "object" === a(e) && (e = Q(re(e, t), t)), e
            }

            function ie(e, t, r) {
                return "string" == typeof e ? e = re(Q(e, r), r) : "object" === a(e) && (e = re(e, r)), "string" == typeof t ? t = re(Q(t, r), r) : "object" === a(t) && (t = re(t, r)), e === t
            }

            function se(e, t) {
                return e && e.toString().replace(t && t.iri ? c.ESCAPE : l.ESCAPE, H)
            }

            function le(e, t) {
                return e && e.toString().replace(t && t.iri ? c.PCT_ENCODED : l.PCT_ENCODED, q)
            }
            var ce = {
                    scheme: "http",
                    domainHost: !0,
                    parse: function(e, t) {
                        return e.host || (e.error = e.error || "HTTP URIs must have a host."), e
                    },
                    serialize: function(e, t) {
                        var r = "https" === String(e.scheme).toLowerCase();
                        return e.port !== (r ? 443 : 80) && "" !== e.port || (e.port = void 0), e.path || (e.path = "/"), e
                    }
                },
                ue = {
                    scheme: "https",
                    domainHost: ce.domainHost,
                    parse: ce.parse,
                    serialize: ce.serialize
                };

            function de(e) {
                return "boolean" == typeof e.secure ? e.secure : "wss" === String(e.scheme).toLowerCase()
            }
            var he = {
                    scheme: "ws",
                    domainHost: !0,
                    parse: function(e, t) {
                        var r = e;
                        return r.secure = de(r), r.resourceName = (r.path || "/") + (r.query ? "?" + r.query : ""), r.path = void 0, r.query = void 0, r
                    },
                    serialize: function(e, t) {
                        if (e.port !== (de(e) ? 443 : 80) && "" !== e.port || (e.port = void 0), "boolean" == typeof e.secure && (e.scheme = e.secure ? "wss" : "ws", e.secure = void 0), e.resourceName) {
                            var r = e.resourceName.split("?"),
                                a = u(r, 2),
                                n = a[0],
                                o = a[1];
                            e.path = n && "/" !== n ? n : void 0, e.query = o, e.resourceName = void 0
                        }
                        return e.fragment = void 0, e
                    }
                },
                pe = {
                    scheme: "wss",
                    domainHost: he.domainHost,
                    parse: he.parse,
                    serialize: he.serialize
                },
                fe = {},
                me = "[A-Za-z0-9\\-\\.\\_\\~\\xA0-\\u200D\\u2010-\\u2029\\u202F-\\uD7FF\\uF900-\\uFDCF\\uFDF0-\\uFFEF]",
                ve = "[0-9A-Fa-f]",
                ge = r(r("%[EFef]" + ve + "%" + ve + ve + "%" + ve + ve) + "|" + r("%[89A-Fa-f]" + ve + "%" + ve + ve) + "|" + r("%" + ve + ve)),
                ye = "[A-Za-z0-9\\!\\$\\%\\'\\*\\+\\-\\^\\_\\`\\{\\|\\}\\~]",
                be = t("[\\!\\$\\%\\'\\(\\)\\*\\+\\,\\-\\.0-9\\<\\>A-Z\\x5E-\\x7E]", '[\\"\\\\]'),
                we = "[\\!\\$\\'\\(\\)\\*\\+\\,\\;\\:\\@]",
                Ee = new RegExp(me, "g"),
                Pe = new RegExp(ge, "g"),
                ke = new RegExp(t("[^]", ye, "[\\.]", '[\\"]', be), "g"),
                _e = new RegExp(t("[^]", me, we), "g"),
                Se = _e;

            function Ce(e) {
                var t = q(e);
                return t.match(Ee) ? t : e
            }
            var Te = {
                    scheme: "mailto",
                    parse: function(e, t) {
                        var r = e,
                            a = r.to = r.path ? r.path.split(",") : [];
                        if (r.path = void 0, r.query) {
                            for (var n = !1, o = {}, i = r.query.split("&"), s = 0, l = i.length; s < l; ++s) {
                                var c = i[s].split("=");
                                switch (c[0]) {
                                    case "to":
                                        for (var u = c[1].split(","), d = 0, h = u.length; d < h; ++d) a.push(u[d]);
                                        break;
                                    case "subject":
                                        r.subject = le(c[1], t);
                                        break;
                                    case "body":
                                        r.body = le(c[1], t);
                                        break;
                                    default:
                                        n = !0, o[le(c[0], t)] = le(c[1], t)
                                }
                            }
                            n && (r.headers = o)
                        }
                        r.query = void 0;
                        for (var p = 0, f = a.length; p < f; ++p) {
                            var m = a[p].split("@");
                            if (m[0] = le(m[0]), t.unicodeSupport) m[1] = le(m[1], t).toLowerCase();
                            else try {
                                m[1] = j.toASCII(le(m[1], t).toLowerCase())
                            } catch (e) {
                                r.error = r.error || "Email address's domain name can not be converted to ASCII via punycode: " + e
                            }
                            a[p] = m.join("@")
                        }
                        return r
                    },
                    serialize: function(e, t) {
                        var r = e,
                            a = o(e.to);
                        if (a) {
                            for (var i = 0, s = a.length; i < s; ++i) {
                                var l = String(a[i]),
                                    c = l.lastIndexOf("@"),
                                    u = l.slice(0, c).replace(Pe, Ce).replace(Pe, n).replace(ke, H),
                                    d = l.slice(c + 1);
                                try {
                                    d = t.iri ? j.toUnicode(d) : j.toASCII(le(d, t).toLowerCase())
                                } catch (e) {
                                    r.error = r.error || "Email address's domain name can not be converted to " + (t.iri ? "Unicode" : "ASCII") + " via punycode: " + e
                                }
                                a[i] = u + "@" + d
                            }
                            r.path = a.join(",")
                        }
                        var h = e.headers = e.headers || {};
                        e.subject && (h.subject = e.subject), e.body && (h.body = e.body);
                        var p = [];
                        for (var f in h) h[f] !== fe[f] && p.push(f.replace(Pe, Ce).replace(Pe, n).replace(_e, H) + "=" + h[f].replace(Pe, Ce).replace(Pe, n).replace(Se, H));
                        return p.length && (r.query = p.join("&")), r
                    }
                },
                xe = /^([^\:]+)\:(.*)/,
                De = {
                    scheme: "urn",
                    parse: function(e, t) {
                        var r = e.path && e.path.match(xe),
                            a = e;
                        if (r) {
                            var n = t.scheme || a.scheme || "urn",
                                o = r[1].toLowerCase(),
                                i = r[2],
                                s = n + ":" + (t.nid || o),
                                l = U[s];
                            a.nid = o, a.nss = i, a.path = void 0, l && (a = l.parse(a, t))
                        } else a.error = a.error || "URN can not be parsed.";
                        return a
                    },
                    serialize: function(e, t) {
                        var r = t.scheme || e.scheme || "urn",
                            a = e.nid,
                            n = r + ":" + (t.nid || a),
                            o = U[n];
                        o && (e = o.serialize(e, t));
                        var i = e,
                            s = e.nss;
                        return i.path = (a || t.nid) + ":" + s, i
                    }
                },
                Oe = /^[0-9A-Fa-f]{8}(?:\-[0-9A-Fa-f]{4}){3}\-[0-9A-Fa-f]{12}$/,
                Re = {
                    scheme: "urn:uuid",
                    parse: function(e, t) {
                        var r = e;
                        return r.uuid = r.nss, r.nss = void 0, t.tolerant || r.uuid && r.uuid.match(Oe) || (r.error = r.error || "UUID is not valid."), r
                    },
                    serialize: function(e, t) {
                        var r = e;
                        return r.nss = (e.uuid || "").toLowerCase(), r
                    }
                };
            U[ce.scheme] = ce, U[ue.scheme] = ue, U[he.scheme] = he, U[pe.scheme] = pe, U[Te.scheme] = Te, U[De.scheme] = De, U[Re.scheme] = Re, e.SCHEMES = U, e.pctEncChar = H, e.pctDecChars = q, e.parse = Q, e.removeDotSegments = te, e.serialize = re, e.resolveComponents = ae, e.resolve = ne, e.normalize = oe, e.equal = ie, e.escapeComponent = se, e.unescapeComponent = le, Object.defineProperty(e, "__esModule", {
                value: !0
            })
        }(t)
    })),
    hs = function e(t, r) {
        if (t === r) return !0;
        if (t && r && "object" == typeof t && "object" == typeof r) {
            if (t.constructor !== r.constructor) return !1;
            var a, n, o;
            if (Array.isArray(t)) {
                if ((a = t.length) != r.length) return !1;
                for (n = a; 0 != n--;)
                    if (!e(t[n], r[n])) return !1;
                return !0
            }
            if (t.constructor === RegExp) return t.source === r.source && t.flags === r.flags;
            if (t.valueOf !== Object.prototype.valueOf) return t.valueOf() === r.valueOf();
            if (t.toString !== Object.prototype.toString) return t.toString() === r.toString();
            if ((a = (o = Object.keys(t)).length) !== Object.keys(r).length) return !1;
            for (n = a; 0 != n--;)
                if (!Object.prototype.hasOwnProperty.call(r, o[n])) return !1;
            for (n = a; 0 != n--;) {
                var i = o[n];
                if (!e(t[i], r[i])) return !1
            }
            return !0
        }
        return t != t && r != r
    },
    ps = {
        copy: function(e, t) {
            for (var r in t = t || {}, e) t[r] = e[r];
            return t
        },
        checkDataType: fs,
        checkDataTypes: function(e, t, r) {
            switch (e.length) {
                case 1:
                    return fs(e[0], t, r, !0);
                default:
                    var a = "",
                        n = vs(e);
                    for (var o in n.array && n.object && (a = n.null ? "(" : "(!" + t + " || ", a += "typeof " + t + ' !== "object")', delete n.null, delete n.array, delete n.object), n.number && delete n.integer, n) a += (a ? " && " : "") + fs(o, t, r, !0);
                    return a
            }
        },
        coerceToTypes: function(e, t) {
            if (Array.isArray(t)) {
                for (var r = [], a = 0; a < t.length; a++) {
                    var n = t[a];
                    (ms[n] || "array" === e && "array" === n) && (r[r.length] = n)
                }
                if (r.length) return r
            } else {
                if (ms[t]) return [t];
                if ("array" === e && "array" === t) return ["array"]
            }
        },
        toHash: vs,
        getProperty: bs,
        escapeQuotes: ws,
        equal: hs,
        ucs2length: function(e) {
            for (var t, r = 0, a = e.length, n = 0; n < a;) r++, (t = e.charCodeAt(n++)) >= 55296 && t <= 56319 && n < a && 56320 == (64512 & (t = e.charCodeAt(n))) && n++;
            return r
        },
        varOccurences: function(e, t) {
            t += "[^0-9]";
            var r = e.match(new RegExp(t, "g"));
            return r ? r.length : 0
        },
        varReplace: function(e, t, r) {
            return t += "([^0-9])", r = r.replace(/\$/g, "$$$$"), e.replace(new RegExp(t, "g"), r + "$1")
        },
        schemaHasRules: function(e, t) {
            if ("boolean" == typeof e) return !e;
            for (var r in e)
                if (t[r]) return !0
        },
        schemaHasRulesExcept: function(e, t, r) {
            if ("boolean" == typeof e) return !e && "not" != r;
            for (var a in e)
                if (a != r && t[a]) return !0
        },
        schemaUnknownRules: function(e, t) {
            if ("boolean" == typeof e) return;
            for (var r in e)
                if (!t[r]) return r
        },
        toQuotedString: Es,
        getPathExpr: function(e, t, r, a) {
            return _s(e, r ? "'/' + " + t + (a ? "" : ".replace(/~/g, '~0').replace(/\\//g, '~1')") : a ? "'[' + " + t + " + ']'" : "'[\\'' + " + t + " + '\\']'")
        },
        getPath: function(e, t, r) {
            var a = Es(r ? "/" + Ss(t) : bs(t));
            return _s(e, a)
        },
        getData: function(e, t, r) {
            var a, n, o, i;
            if ("" === e) return "rootData";
            if ("/" == e[0]) {
                if (!Ps.test(e)) throw new Error("Invalid JSON-pointer: " + e);
                n = e, o = "rootData"
            } else {
                if (!(i = e.match(ks))) throw new Error("Invalid JSON-pointer: " + e);
                if (a = +i[1], "#" == (n = i[2])) {
                    if (a >= t) throw new Error("Cannot access property/index " + a + " levels up, current level is " + t);
                    return r[t - a]
                }
                if (a > t) throw new Error("Cannot access data " + a + " levels up, current level is " + t);
                if (o = "data" + (t - a || ""), !n) return o
            }
            for (var s = o, l = n.split("/"), c = 0; c < l.length; c++) {
                var u = l[c];
                u && (o += bs(Cs(u)), s += " && " + o)
            }
            return s
        },
        unescapeFragment: function(e) {
            return Cs(decodeURIComponent(e))
        },
        unescapeJsonPointer: Cs,
        escapeFragment: function(e) {
            return encodeURIComponent(Ss(e))
        },
        escapeJsonPointer: Ss
    };

function fs(e, t, r, a) {
    var n = a ? " !== " : " === ",
        o = a ? " || " : " && ",
        i = a ? "!" : "",
        s = a ? "" : "!";
    switch (e) {
        case "null":
            return t + n + "null";
        case "array":
            return i + "Array.isArray(" + t + ")";
        case "object":
            return "(" + i + t + o + "typeof " + t + n + '"object"' + o + s + "Array.isArray(" + t + "))";
        case "integer":
            return "(typeof " + t + n + '"number"' + o + s + "(" + t + " % 1)" + o + t + n + t + (r ? o + i + "isFinite(" + t + ")" : "") + ")";
        case "number":
            return "(typeof " + t + n + '"' + e + '"' + (r ? o + i + "isFinite(" + t + ")" : "") + ")";
        default:
            return "typeof " + t + n + '"' + e + '"'
    }
}
var ms = vs(["string", "number", "integer", "boolean", "null"]);

function vs(e) {
    for (var t = {}, r = 0; r < e.length; r++) t[e[r]] = !0;
    return t
}
var gs = /^[a-z$_][a-z$_0-9]*$/i,
    ys = /'|\\/g;

function bs(e) {
    return "number" == typeof e ? "[" + e + "]" : gs.test(e) ? "." + e : "['" + ws(e) + "']"
}

function ws(e) {
    return e.replace(ys, "\\$&").replace(/\n/g, "\\n").replace(/\r/g, "\\r").replace(/\f/g, "\\f").replace(/\t/g, "\\t")
}

function Es(e) {
    return "'" + ws(e) + "'"
}
var Ps = /^\/(?:[^~]|~0|~1)*$/,
    ks = /^([0-9]+)(#|\/(?:[^~]|~0|~1)*)?$/;

function _s(e, t) {
    return '""' == e ? t : (e + " + " + t).replace(/([^\\])' \+ '/g, "$1")
}

function Ss(e) {
    return e.replace(/~/g, "~0").replace(/\//g, "~1")
}

function Cs(e) {
    return e.replace(/~1/g, "/").replace(/~0/g, "~")
}
var Ts = function(e) {
    ps.copy(e, this)
};
var xs = us((function(e) {
        var t = e.exports = function(e, t, a) {
            "function" == typeof t && (a = t, t = {}), r(t, "function" == typeof(a = t.cb || a) ? a : a.pre || function() {}, a.post || function() {}, e, "", e)
        };

        function r(e, a, n, o, i, s, l, c, u, d) {
            if (o && "object" == typeof o && !Array.isArray(o)) {
                for (var h in a(o, i, s, l, c, u, d), o) {
                    var p = o[h];
                    if (Array.isArray(p)) {
                        if (h in t.arrayKeywords)
                            for (var f = 0; f < p.length; f++) r(e, a, n, p[f], i + "/" + h + "/" + f, s, i, h, o, f)
                    } else if (h in t.propsKeywords) {
                        if (p && "object" == typeof p)
                            for (var m in p) r(e, a, n, p[m], i + "/" + h + "/" + m.replace(/~/g, "~0").replace(/\//g, "~1"), s, i, h, o, m)
                    } else(h in t.keywords || e.allKeys && !(h in t.skipKeywords)) && r(e, a, n, p, i + "/" + h, s, i, h, o)
                }
                n(o, i, s, l, c, u, d)
            }
        }
        t.keywords = {
            additionalItems: !0,
            items: !0,
            contains: !0,
            additionalProperties: !0,
            propertyNames: !0,
            not: !0
        }, t.arrayKeywords = {
            items: !0,
            allOf: !0,
            anyOf: !0,
            oneOf: !0
        }, t.propsKeywords = {
            definitions: !0,
            properties: !0,
            patternProperties: !0,
            dependencies: !0
        }, t.skipKeywords = {
            default: !0,
            enum: !0,
            const: !0,
            required: !0,
            maximum: !0,
            minimum: !0,
            exclusiveMaximum: !0,
            exclusiveMinimum: !0,
            multipleOf: !0,
            maxLength: !0,
            minLength: !0,
            pattern: !0,
            format: !0,
            maxItems: !0,
            minItems: !0,
            uniqueItems: !0,
            maxProperties: !0,
            minProperties: !0
        }
    })),
    Ds = Os;

function Os(e, t, r) {
    var a = this._refs[r];
    if ("string" == typeof a) {
        if (!this._refs[a]) return Os.call(this, e, t, a);
        a = this._refs[a]
    }
    if ((a = a || this._schemas[r]) instanceof Ts) return Ls(a.schema, this._opts.inlineRefs) ? a.schema : a.validate || this._compile(a);
    var n, o, i, s = Rs.call(this, t, r);
    return s && (n = s.schema, t = s.root, i = s.baseId), n instanceof Ts ? o = n.validate || e.call(this, n.schema, t, void 0, i) : void 0 !== n && (o = Ls(n, this._opts.inlineRefs) ? n : e.call(this, n, t, void 0, i)), o
}

function Rs(e, t) {
    var r = ds.parse(t),
        a = Us(r),
        n = js(this._getId(e.schema));
    if (0 === Object.keys(e.schema).length || a !== n) {
        var o = qs(a),
            i = this._refs[o];
        if ("string" == typeof i) return Fs.call(this, e, i, r);
        if (i instanceof Ts) i.validate || this._compile(i), e = i;
        else {
            if (!((i = this._schemas[o]) instanceof Ts)) return;
            if (i.validate || this._compile(i), o == qs(t)) return {
                schema: i,
                root: e,
                baseId: n
            };
            e = i
        }
        if (!e.schema) return;
        n = js(this._getId(e.schema))
    }
    return As.call(this, r, n, e.schema, e)
}

function Fs(e, t, r) {
    var a = Rs.call(this, e, t);
    if (a) {
        var n = a.schema,
            o = a.baseId;
        e = a.root;
        var i = this._getId(n);
        return i && (o = Ys(o, i)), As.call(this, r, o, n, e)
    }
}
Os.normalizeId = qs, Os.fullPath = js, Os.url = Ys, Os.ids = function(e) {
    var t = qs(this._getId(e)),
        r = {
            "": t
        },
        a = {
            "": js(t, !1)
        },
        n = {},
        o = this;
    return xs(e, {
        allKeys: !0
    }, (function(e, t, i, s, l, c, u) {
        if ("" !== t) {
            var d = o._getId(e),
                h = r[s],
                p = a[s] + "/" + l;
            if (void 0 !== u && (p += "/" + ("number" == typeof u ? u : ps.escapeFragment(u))), "string" == typeof d) {
                d = h = qs(h ? ds.resolve(h, d) : d);
                var f = o._refs[d];
                if ("string" == typeof f && (f = o._refs[f]), f && f.schema) {
                    if (!hs(e, f.schema)) throw new Error('id "' + d + '" resolves to more than one schema')
                } else if (d != qs(p))
                    if ("#" == d[0]) {
                        if (n[d] && !hs(e, n[d])) throw new Error('id "' + d + '" resolves to more than one schema');
                        n[d] = e
                    } else o._refs[d] = p
            }
            r[t] = h, a[t] = p
        }
    })), n
}, Os.inlineRef = Ls, Os.schema = Rs;
var $s = ps.toHash(["properties", "patternProperties", "enum", "dependencies", "definitions"]);

function As(e, t, r, a) {
    if (e.fragment = e.fragment || "", "/" == e.fragment.slice(0, 1)) {
        for (var n = e.fragment.split("/"), o = 1; o < n.length; o++) {
            var i = n[o];
            if (i) {
                if (void 0 === (r = r[i = ps.unescapeFragment(i)])) break;
                var s;
                if (!$s[i] && ((s = this._getId(r)) && (t = Ys(t, s)), r.$ref)) {
                    var l = Ys(t, r.$ref),
                        c = Rs.call(this, a, l);
                    c && (r = c.schema, a = c.root, t = c.baseId)
                }
            }
        }
        return void 0 !== r && r !== a.schema ? {
            schema: r,
            root: a,
            baseId: t
        } : void 0
    }
}
var Ms = ps.toHash(["type", "format", "pattern", "maxLength", "minLength", "maxProperties", "minProperties", "maxItems", "minItems", "maximum", "minimum", "uniqueItems", "multipleOf", "required", "enum"]);

function Ls(e, t) {
    return !1 !== t && (void 0 === t || !0 === t ? Ns(e) : t ? Is(e) <= t : void 0)
}

function Ns(e) {
    var t;
    if (Array.isArray(e)) {
        for (var r = 0; r < e.length; r++)
            if ("object" == typeof(t = e[r]) && !Ns(t)) return !1
    } else
        for (var a in e) {
            if ("$ref" == a) return !1;
            if ("object" == typeof(t = e[a]) && !Ns(t)) return !1
        }
    return !0
}

function Is(e) {
    var t, r = 0;
    if (Array.isArray(e)) {
        for (var a = 0; a < e.length; a++)
            if ("object" == typeof(t = e[a]) && (r += Is(t)), r == 1 / 0) return 1 / 0
    } else
        for (var n in e) {
            if ("$ref" == n) return 1 / 0;
            if (Ms[n]) r++;
            else if ("object" == typeof(t = e[n]) && (r += Is(t) + 1), r == 1 / 0) return 1 / 0
        }
    return r
}

function js(e, t) {
    return !1 !== t && (e = qs(e)), Us(ds.parse(e))
}

function Us(e) {
    return ds.serialize(e).split("#")[0] + "#"
}
var Hs = /#\/?$/;

function qs(e) {
    return e ? e.replace(Hs, "") : ""
}

function Ys(e, t) {
    return t = qs(t), ds.resolve(e, t)
}
var Bs = {
    Validation: Vs((function(e) {
        this.message = "validation failed", this.errors = e, this.ajv = this.validation = !0
    })),
    MissingRef: Vs(Ws)
};

function Ws(e, t, r) {
    this.message = r || Ws.message(e, t), this.missingRef = Ds.url(e, t), this.missingSchema = Ds.normalizeId(Ds.fullPath(this.missingRef))
}

function Vs(e) {
    return e.prototype = Object.create(Error.prototype), e.prototype.constructor = e, e
}
Ws.message = function(e, t) {
    return "can't resolve reference " + t + " from id " + e
};
var zs = function(e, t) {
        t || (t = {}), "function" == typeof t && (t = {
            cmp: t
        });
        var r, a = "boolean" == typeof t.cycles && t.cycles,
            n = t.cmp && (r = t.cmp, function(e) {
                return function(t, a) {
                    var n = {
                            key: t,
                            value: e[t]
                        },
                        o = {
                            key: a,
                            value: e[a]
                        };
                    return r(n, o)
                }
            }),
            o = [];
        return function e(t) {
            if (t && t.toJSON && "function" == typeof t.toJSON && (t = t.toJSON()), void 0 !== t) {
                if ("number" == typeof t) return isFinite(t) ? "" + t : "null";
                if ("object" != typeof t) return JSON.stringify(t);
                var r, i;
                if (Array.isArray(t)) {
                    for (i = "[", r = 0; r < t.length; r++) r && (i += ","), i += e(t[r]) || "null";
                    return i + "]"
                }
                if (null === t) return "null";
                if (-1 !== o.indexOf(t)) {
                    if (a) return JSON.stringify("__cycle__");
                    throw new TypeError("Converting circular structure to JSON")
                }
                var s = o.push(t) - 1,
                    l = Object.keys(t).sort(n && n(t));
                for (i = "", r = 0; r < l.length; r++) {
                    var c = l[r],
                        u = e(t[c]);
                    u && (i && (i += ","), i += JSON.stringify(c) + ":" + u)
                }
                return o.splice(s, 1), "{" + i + "}"
            }
        }(e)
    },
    Xs = function(e, t, r) {
        var a = "",
            n = !0 === e.schema.$async,
            o = e.util.schemaHasRulesExcept(e.schema, e.RULES.all, "$ref"),
            i = e.self._getId(e.schema);
        if (e.opts.strictKeywords) {
            var s = e.util.schemaUnknownRules(e.schema, e.RULES.keywords);
            if (s) {
                var l = "unknown keyword: " + s;
                if ("log" !== e.opts.strictKeywords) throw new Error(l);
                e.logger.warn(l)
            }
        }
        if (e.isTop && (a += " var validate = ", n && (e.async = !0, a += "async "), a += "function(data, dataPath, parentData, parentDataProperty, rootData) { 'use strict'; ", i && (e.opts.sourceCode || e.opts.processCode) && (a += " /*# sourceURL=" + i + " */ ")), "boolean" == typeof e.schema || !o && !e.schema.$ref) {
            t = "false schema";
            var c = e.level,
                u = e.dataLevel,
                d = e.schema[t],
                h = e.schemaPath + e.util.getProperty(t),
                p = e.errSchemaPath + "/" + t,
                f = !e.opts.allErrors,
                m = "data" + (u || ""),
                v = "valid" + c;
            if (!1 === e.schema) {
                e.isTop ? f = !0 : a += " var " + v + " = false; ", (G = G || []).push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'false schema' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(p) + " , params: {} ", !1 !== e.opts.messages && (a += " , message: 'boolean schema is false' "), e.opts.verbose && (a += " , schema: false , parentSchema: validate.schema" + e.schemaPath + " , data: " + m + " "), a += " } ") : a += " {} ";
                var g = a;
                a = G.pop(), !e.compositeRule && f ? e.async ? a += " throw new ValidationError([" + g + "]); " : a += " validate.errors = [" + g + "]; return false; " : a += " var err = " + g + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; "
            } else e.isTop ? a += n ? " return data; " : " validate.errors = null; return true; " : a += " var " + v + " = true; ";
            return e.isTop && (a += " }; return validate; "), a
        }
        if (e.isTop) {
            var y = e.isTop;
            c = e.level = 0, u = e.dataLevel = 0, m = "data";
            if (e.rootId = e.resolve.fullPath(e.self._getId(e.root.schema)), e.baseId = e.baseId || e.rootId, delete e.isTop, e.dataPathArr = [""], void 0 !== e.schema.default && e.opts.useDefaults && e.opts.strictDefaults) {
                var b = "default is ignored in the schema root";
                if ("log" !== e.opts.strictDefaults) throw new Error(b);
                e.logger.warn(b)
            }
            a += " var vErrors = null; ", a += " var errors = 0;     ", a += " if (rootData === undefined) rootData = data; "
        } else {
            c = e.level, m = "data" + ((u = e.dataLevel) || "");
            if (i && (e.baseId = e.resolve.url(e.baseId, i)), n && !e.async) throw new Error("async schema in sync schema");
            a += " var errs_" + c + " = errors;"
        }
        v = "valid" + c, f = !e.opts.allErrors;
        var w = "",
            E = "",
            P = e.schema.type,
            k = Array.isArray(P);
        if (P && e.opts.nullable && !0 === e.schema.nullable && (k ? -1 == P.indexOf("null") && (P = P.concat("null")) : "null" != P && (P = [P, "null"], k = !0)), k && 1 == P.length && (P = P[0], k = !1), e.schema.$ref && o) {
            if ("fail" == e.opts.extendRefs) throw new Error('$ref: validation keywords used in schema at path "' + e.errSchemaPath + '" (see option extendRefs)');
            !0 !== e.opts.extendRefs && (o = !1, e.logger.warn('$ref: keywords ignored in schema at path "' + e.errSchemaPath + '"'))
        }
        if (e.schema.$comment && e.opts.$comment && (a += " " + e.RULES.all.$comment.code(e, "$comment")), P) {
            if (e.opts.coerceTypes) var _ = e.util.coerceToTypes(e.opts.coerceTypes, P);
            var S = e.RULES.types[P];
            if (_ || k || !0 === S || S && !K(S)) {
                h = e.schemaPath + ".type", p = e.errSchemaPath + "/type", h = e.schemaPath + ".type", p = e.errSchemaPath + "/type";
                var C = k ? "checkDataTypes" : "checkDataType";
                if (a += " if (" + e.util[C](P, m, e.opts.strictNumbers, !0) + ") { ", _) {
                    var T = "dataType" + c,
                        x = "coerced" + c;
                    a += " var " + T + " = typeof " + m + "; var " + x + " = undefined; ", "array" == e.opts.coerceTypes && (a += " if (" + T + " == 'object' && Array.isArray(" + m + ") && " + m + ".length == 1) { " + m + " = " + m + "[0]; " + T + " = typeof " + m + "; if (" + e.util.checkDataType(e.schema.type, m, e.opts.strictNumbers) + ") " + x + " = " + m + "; } "), a += " if (" + x + " !== undefined) ; ";
                    var D = _;
                    if (D)
                        for (var O, R = -1, F = D.length - 1; R < F;) "string" == (O = D[R += 1]) ? a += " else if (" + T + " == 'number' || " + T + " == 'boolean') " + x + " = '' + " + m + "; else if (" + m + " === null) " + x + " = ''; " : "number" == O || "integer" == O ? (a += " else if (" + T + " == 'boolean' || " + m + " === null || (" + T + " == 'string' && " + m + " && " + m + " == +" + m + " ", "integer" == O && (a += " && !(" + m + " % 1)"), a += ")) " + x + " = +" + m + "; ") : "boolean" == O ? a += " else if (" + m + " === 'false' || " + m + " === 0 || " + m + " === null) " + x + " = false; else if (" + m + " === 'true' || " + m + " === 1) " + x + " = true; " : "null" == O ? a += " else if (" + m + " === '' || " + m + " === 0 || " + m + " === false) " + x + " = null; " : "array" == e.opts.coerceTypes && "array" == O && (a += " else if (" + T + " == 'string' || " + T + " == 'number' || " + T + " == 'boolean' || " + m + " == null) " + x + " = [" + m + "]; ");
                    a += " else {   ", (G = G || []).push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'type' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(p) + " , params: { type: '", a += k ? "" + P.join(",") : "" + P, a += "' } ", !1 !== e.opts.messages && (a += " , message: 'should be ", a += k ? "" + P.join(",") : "" + P, a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + h + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + m + " "), a += " } ") : a += " {} ";
                    g = a;
                    a = G.pop(), !e.compositeRule && f ? e.async ? a += " throw new ValidationError([" + g + "]); " : a += " validate.errors = [" + g + "]; return false; " : a += " var err = " + g + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " } if (" + x + " !== undefined) {  ";
                    var $ = u ? "data" + (u - 1 || "") : "parentData";
                    a += " " + m + " = " + x + "; ", u || (a += "if (" + $ + " !== undefined)"), a += " " + $ + "[" + (u ? e.dataPathArr[u] : "parentDataProperty") + "] = " + x + "; } "
                } else {
                    (G = G || []).push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'type' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(p) + " , params: { type: '", a += k ? "" + P.join(",") : "" + P, a += "' } ", !1 !== e.opts.messages && (a += " , message: 'should be ", a += k ? "" + P.join(",") : "" + P, a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + h + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + m + " "), a += " } ") : a += " {} ";
                    g = a;
                    a = G.pop(), !e.compositeRule && f ? e.async ? a += " throw new ValidationError([" + g + "]); " : a += " validate.errors = [" + g + "]; return false; " : a += " var err = " + g + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; "
                }
                a += " } "
            }
        }
        if (e.schema.$ref && !o) a += " " + e.RULES.all.$ref.code(e, "$ref") + " ", f && (a += " } if (errors === ", a += y ? "0" : "errs_" + c, a += ") { ", E += "}");
        else {
            var A = e.RULES;
            if (A)
                for (var M = -1, L = A.length - 1; M < L;)
                    if (K(S = A[M += 1])) {
                        if (S.type && (a += " if (" + e.util.checkDataType(S.type, m, e.opts.strictNumbers) + ") { "), e.opts.useDefaults)
                            if ("object" == S.type && e.schema.properties) {
                                d = e.schema.properties;
                                var N = Object.keys(d);
                                if (N)
                                    for (var I, j = -1, U = N.length - 1; j < U;) {
                                        if (void 0 !== (Y = d[I = N[j += 1]]).default) {
                                            var H = m + e.util.getProperty(I);
                                            if (e.compositeRule) {
                                                if (e.opts.strictDefaults) {
                                                    b = "default is ignored for: " + H;
                                                    if ("log" !== e.opts.strictDefaults) throw new Error(b);
                                                    e.logger.warn(b)
                                                }
                                            } else a += " if (" + H + " === undefined ", "empty" == e.opts.useDefaults && (a += " || " + H + " === null || " + H + " === '' "), a += " ) " + H + " = ", "shared" == e.opts.useDefaults ? a += " " + e.useDefault(Y.default) + " " : a += " " + JSON.stringify(Y.default) + " ", a += "; "
                                        }
                                    }
                            } else if ("array" == S.type && Array.isArray(e.schema.items)) {
                            var q = e.schema.items;
                            if (q) {
                                R = -1;
                                for (var Y, B = q.length - 1; R < B;)
                                    if (void 0 !== (Y = q[R += 1]).default) {
                                        H = m + "[" + R + "]";
                                        if (e.compositeRule) {
                                            if (e.opts.strictDefaults) {
                                                b = "default is ignored for: " + H;
                                                if ("log" !== e.opts.strictDefaults) throw new Error(b);
                                                e.logger.warn(b)
                                            }
                                        } else a += " if (" + H + " === undefined ", "empty" == e.opts.useDefaults && (a += " || " + H + " === null || " + H + " === '' "), a += " ) " + H + " = ", "shared" == e.opts.useDefaults ? a += " " + e.useDefault(Y.default) + " " : a += " " + JSON.stringify(Y.default) + " ", a += "; "
                                    }
                            }
                        }
                        var W = S.rules;
                        if (W)
                            for (var V, z = -1, X = W.length - 1; z < X;)
                                if (J(V = W[z += 1])) {
                                    var Q = V.code(e, V.keyword, S.type);
                                    Q && (a += " " + Q + " ", f && (w += "}"))
                                } if (f && (a += " " + w + " ", w = ""), S.type && (a += " } ", P && P === S.type && !_)) {
                            a += " else { ";
                            var G;
                            h = e.schemaPath + ".type", p = e.errSchemaPath + "/type";
                            (G = G || []).push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'type' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(p) + " , params: { type: '", a += k ? "" + P.join(",") : "" + P, a += "' } ", !1 !== e.opts.messages && (a += " , message: 'should be ", a += k ? "" + P.join(",") : "" + P, a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + h + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + m + " "), a += " } ") : a += " {} ";
                            g = a;
                            a = G.pop(), !e.compositeRule && f ? e.async ? a += " throw new ValidationError([" + g + "]); " : a += " validate.errors = [" + g + "]; return false; " : a += " var err = " + g + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " } "
                        }
                        f && (a += " if (errors === ", a += y ? "0" : "errs_" + c, a += ") { ", E += "}")
                    }
        }

        function K(e) {
            for (var t = e.rules, r = 0; r < t.length; r++)
                if (J(t[r])) return !0
        }

        function J(t) {
            return void 0 !== e.schema[t.keyword] || t.implements && function(t) {
                for (var r = t.implements, a = 0; a < r.length; a++)
                    if (void 0 !== e.schema[r[a]]) return !0
            }(t)
        }
        return f && (a += " " + E + " "), y ? (n ? (a += " if (errors === 0) return data;           ", a += " else throw new ValidationError(vErrors); ") : (a += " validate.errors = vErrors; ", a += " return errors === 0;       "), a += " }; return validate;") : a += " var " + v + " = errors === errs_" + c + ";", a
    },
    Qs = ps.ucs2length,
    Gs = Bs.Validation,
    Ks = function e(t, r, a, n) {
        var o = this,
            i = this._opts,
            s = [void 0],
            l = {},
            c = [],
            u = {},
            d = [],
            h = {},
            p = [];
        r = r || {
            schema: t,
            refVal: s,
            refs: l
        };
        var f = Js.call(this, t, r, n),
            m = this._compilations[f.index];
        if (f.compiling) return m.callValidate = function e() {
            var t = m.validate,
                r = t.apply(this, arguments);
            return e.errors = t.errors, r
        };
        var v = this._formats,
            g = this.RULES;
        try {
            var y = w(t, r, a, n);
            m.validate = y;
            var b = m.callValidate;
            return b && (b.schema = y.schema, b.errors = null, b.refs = y.refs, b.refVal = y.refVal, b.root = y.root, b.$async = y.$async, i.sourceCode && (b.source = y.source)), y
        } finally {
            Zs.call(this, t, r, n)
        }

        function w(t, a, n, u) {
            var h = !a || a && a.schema == t;
            if (a.schema != r.schema) return e.call(o, t, a, n, u);
            var f, m = !0 === t.$async,
                y = Xs({
                    isTop: !0,
                    schema: t,
                    isRoot: h,
                    baseId: u,
                    root: a,
                    schemaPath: "",
                    errSchemaPath: "#",
                    errorPath: '""',
                    MissingRefError: Bs.MissingRef,
                    RULES: g,
                    validate: Xs,
                    util: ps,
                    resolve: Ds,
                    resolveRef: E,
                    usePattern: _,
                    useDefault: S,
                    useCustomRule: C,
                    opts: i,
                    formats: v,
                    logger: o.logger,
                    self: o
                });
            y = ol(s, al) + ol(c, tl) + ol(d, rl) + ol(p, nl) + y, i.processCode && (y = i.processCode(y, t));
            try {
                f = new Function("self", "RULES", "formats", "root", "refVal", "defaults", "customRules", "equal", "ucs2length", "ValidationError", y)(o, g, v, r, s, d, p, hs, Qs, Gs), s[0] = f
            } catch (e) {
                throw o.logger.error("Error compiling schema, function code:", y), e
            }
            return f.schema = t, f.errors = null, f.refs = l, f.refVal = s, f.root = h ? f : a, m && (f.$async = !0), !0 === i.sourceCode && (f.source = {
                code: y,
                patterns: c,
                defaults: d
            }), f
        }

        function E(t, n, c) {
            n = Ds.url(t, n);
            var u, d, h = l[n];
            if (void 0 !== h) return k(u = s[h], d = "refVal[" + h + "]");
            if (!c && r.refs) {
                var p = r.refs[n];
                if (void 0 !== p) return k(u = r.refVal[p], d = P(n, u))
            }
            d = P(n);
            var f = Ds.call(o, w, r, n);
            if (void 0 === f) {
                var m = a && a[n];
                m && (f = Ds.inlineRef(m, i.inlineRefs) ? m : e.call(o, m, r, a, t))
            }
            if (void 0 !== f) return function(e, t) {
                var r = l[e];
                s[r] = t
            }(n, f), k(f, d);
            ! function(e) {
                delete l[e]
            }(n)
        }

        function P(e, t) {
            var r = s.length;
            return s[r] = t, l[e] = r, "refVal" + r
        }

        function k(e, t) {
            return "object" == typeof e || "boolean" == typeof e ? {
                code: t,
                schema: e,
                inline: !0
            } : {
                code: t,
                $async: e && !!e.$async
            }
        }

        function _(e) {
            var t = u[e];
            return void 0 === t && (t = u[e] = c.length, c[t] = e), "pattern" + t
        }

        function S(e) {
            switch (typeof e) {
                case "boolean":
                case "number":
                    return "" + e;
                case "string":
                    return ps.toQuotedString(e);
                case "object":
                    if (null === e) return "null";
                    var t = zs(e),
                        r = h[t];
                    return void 0 === r && (r = h[t] = d.length, d[r] = e), "default" + r
            }
        }

        function C(e, t, r, a) {
            if (!1 !== o._opts.validateSchema) {
                var n = e.definition.dependencies;
                if (n && !n.every((function(e) {
                        return Object.prototype.hasOwnProperty.call(r, e)
                    }))) throw new Error("parent schema must have all required keywords: " + n.join(","));
                var s = e.definition.validateSchema;
                if (s)
                    if (!s(t)) {
                        var l = "keyword schema is invalid: " + o.errorsText(s.errors);
                        if ("log" != o._opts.validateSchema) throw new Error(l);
                        o.logger.error(l)
                    }
            }
            var c, u = e.definition.compile,
                d = e.definition.inline,
                h = e.definition.macro;
            if (u) c = u.call(o, t, r, a);
            else if (h) c = h.call(o, t, r, a), !1 !== i.validateSchema && o.validateSchema(c, !0);
            else if (d) c = d.call(o, a, e.keyword, t, r);
            else if (!(c = e.definition.validate)) return;
            if (void 0 === c) throw new Error('custom keyword "' + e.keyword + '"failed to compile');
            var f = p.length;
            return p[f] = c, {
                code: "customRule" + f,
                validate: c
            }
        }
    };

function Js(e, t, r) {
    var a = el.call(this, e, t, r);
    return a >= 0 ? {
        index: a,
        compiling: !0
    } : (a = this._compilations.length, this._compilations[a] = {
        schema: e,
        root: t,
        baseId: r
    }, {
        index: a,
        compiling: !1
    })
}

function Zs(e, t, r) {
    var a = el.call(this, e, t, r);
    a >= 0 && this._compilations.splice(a, 1)
}

function el(e, t, r) {
    for (var a = 0; a < this._compilations.length; a++) {
        var n = this._compilations[a];
        if (n.schema == e && n.root == t && n.baseId == r) return a
    }
    return -1
}

function tl(e, t) {
    return "var pattern" + e + " = new RegExp(" + ps.toQuotedString(t[e]) + ");"
}

function rl(e) {
    return "var default" + e + " = defaults[" + e + "];"
}

function al(e, t) {
    return void 0 === t[e] ? "" : "var refVal" + e + " = refVal[" + e + "];"
}

function nl(e) {
    return "var customRule" + e + " = customRules[" + e + "];"
}

function ol(e, t) {
    if (!e.length) return "";
    for (var r = "", a = 0; a < e.length; a++) r += t(a, e);
    return r
}
var il = us((function(e) {
        var t = e.exports = function() {
            this._cache = {}
        };
        t.prototype.put = function(e, t) {
            this._cache[e] = t
        }, t.prototype.get = function(e) {
            return this._cache[e]
        }, t.prototype.del = function(e) {
            delete this._cache[e]
        }, t.prototype.clear = function() {
            this._cache = {}
        }
    })),
    sl = /^(\d\d\d\d)-(\d\d)-(\d\d)$/,
    ll = [0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31],
    cl = /^(\d\d):(\d\d):(\d\d)(\.\d+)?(z|[+-]\d\d(?::?\d\d)?)?$/i,
    ul = /^(?=.{1,253}\.?$)[a-z0-9](?:[a-z0-9-]{0,61}[a-z0-9])?(?:\.[a-z0-9](?:[-0-9a-z]{0,61}[0-9a-z])?)*\.?$/i,
    dl = /^(?:[a-z][a-z0-9+\-.]*:)(?:\/?\/(?:(?:[a-z0-9\-._~!$&'()*+,;=:]|%[0-9a-f]{2})*@)?(?:\[(?:(?:(?:(?:[0-9a-f]{1,4}:){6}|::(?:[0-9a-f]{1,4}:){5}|(?:[0-9a-f]{1,4})?::(?:[0-9a-f]{1,4}:){4}|(?:(?:[0-9a-f]{1,4}:){0,1}[0-9a-f]{1,4})?::(?:[0-9a-f]{1,4}:){3}|(?:(?:[0-9a-f]{1,4}:){0,2}[0-9a-f]{1,4})?::(?:[0-9a-f]{1,4}:){2}|(?:(?:[0-9a-f]{1,4}:){0,3}[0-9a-f]{1,4})?::[0-9a-f]{1,4}:|(?:(?:[0-9a-f]{1,4}:){0,4}[0-9a-f]{1,4})?::)(?:[0-9a-f]{1,4}:[0-9a-f]{1,4}|(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?))|(?:(?:[0-9a-f]{1,4}:){0,5}[0-9a-f]{1,4})?::[0-9a-f]{1,4}|(?:(?:[0-9a-f]{1,4}:){0,6}[0-9a-f]{1,4})?::)|[Vv][0-9a-f]+\.[a-z0-9\-._~!$&'()*+,;=:]+)\]|(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?)|(?:[a-z0-9\-._~!$&'()*+,;=]|%[0-9a-f]{2})*)(?::\d*)?(?:\/(?:[a-z0-9\-._~!$&'()*+,;=:@]|%[0-9a-f]{2})*)*|\/(?:(?:[a-z0-9\-._~!$&'()*+,;=:@]|%[0-9a-f]{2})+(?:\/(?:[a-z0-9\-._~!$&'()*+,;=:@]|%[0-9a-f]{2})*)*)?|(?:[a-z0-9\-._~!$&'()*+,;=:@]|%[0-9a-f]{2})+(?:\/(?:[a-z0-9\-._~!$&'()*+,;=:@]|%[0-9a-f]{2})*)*)(?:\?(?:[a-z0-9\-._~!$&'()*+,;=:@/?]|%[0-9a-f]{2})*)?(?:#(?:[a-z0-9\-._~!$&'()*+,;=:@/?]|%[0-9a-f]{2})*)?$/i,
    hl = /^(?:(?:[^\x00-\x20"'<>%\\^`{|}]|%[0-9a-f]{2})|\{[+#./;?&=,!@|]?(?:[a-z0-9_]|%[0-9a-f]{2})+(?::[1-9][0-9]{0,3}|\*)?(?:,(?:[a-z0-9_]|%[0-9a-f]{2})+(?::[1-9][0-9]{0,3}|\*)?)*\})*$/i,
    pl = /^(?:(?:http[s\u017F]?|ftp):\/\/)(?:(?:[\0-\x08\x0E-\x1F!-\x9F\xA1-\u167F\u1681-\u1FFF\u200B-\u2027\u202A-\u202E\u2030-\u205E\u2060-\u2FFF\u3001-\uD7FF\uE000-\uFEFE\uFF00-\uFFFF]|[\uD800-\uDBFF][\uDC00-\uDFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF])+(?::(?:[\0-\x08\x0E-\x1F!-\x9F\xA1-\u167F\u1681-\u1FFF\u200B-\u2027\u202A-\u202E\u2030-\u205E\u2060-\u2FFF\u3001-\uD7FF\uE000-\uFEFE\uFF00-\uFFFF]|[\uD800-\uDBFF][\uDC00-\uDFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF])*)?@)?(?:(?!10(?:\.[0-9]{1,3}){3})(?!127(?:\.[0-9]{1,3}){3})(?!169\.254(?:\.[0-9]{1,3}){2})(?!192\.168(?:\.[0-9]{1,3}){2})(?!172\.(?:1[6-9]|2[0-9]|3[01])(?:\.[0-9]{1,3}){2})(?:[1-9][0-9]?|1[0-9][0-9]|2[01][0-9]|22[0-3])(?:\.(?:1?[0-9]{1,2}|2[0-4][0-9]|25[0-5])){2}(?:\.(?:[1-9][0-9]?|1[0-9][0-9]|2[0-4][0-9]|25[0-4]))|(?:(?:(?:[0-9a-z\xA1-\uD7FF\uE000-\uFFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF])+-)*(?:[0-9a-z\xA1-\uD7FF\uE000-\uFFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF])+)(?:\.(?:(?:[0-9a-z\xA1-\uD7FF\uE000-\uFFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF])+-)*(?:[0-9a-z\xA1-\uD7FF\uE000-\uFFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF])+)*(?:\.(?:(?:[a-z\xA1-\uD7FF\uE000-\uFFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF]){2,})))(?::[0-9]{2,5})?(?:\/(?:[\0-\x08\x0E-\x1F!-\x9F\xA1-\u167F\u1681-\u1FFF\u200B-\u2027\u202A-\u202E\u2030-\u205E\u2060-\u2FFF\u3001-\uD7FF\uE000-\uFEFE\uFF00-\uFFFF]|[\uD800-\uDBFF][\uDC00-\uDFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF])*)?$/i,
    fl = /^(?:urn:uuid:)?[0-9a-f]{8}-(?:[0-9a-f]{4}-){3}[0-9a-f]{12}$/i,
    ml = /^(?:\/(?:[^~/]|~0|~1)*)*$/,
    vl = /^#(?:\/(?:[a-z0-9_\-.!$&'()*+,;:=@]|%[0-9a-f]{2}|~0|~1)*)*$/i,
    gl = /^(?:0|[1-9][0-9]*)(?:#|(?:\/(?:[^~/]|~0|~1)*)*)$/,
    yl = bl;

function bl(e) {
    return e = "full" == e ? "full" : "fast", ps.copy(bl[e])
}

function wl(e) {
    var t = e.match(sl);
    if (!t) return !1;
    var r = +t[1],
        a = +t[2],
        n = +t[3];
    return a >= 1 && a <= 12 && n >= 1 && n <= (2 == a && function(e) {
        return e % 4 == 0 && (e % 100 != 0 || e % 400 == 0)
    }(r) ? 29 : ll[a])
}

function El(e, t) {
    var r = e.match(cl);
    if (!r) return !1;
    var a = r[1],
        n = r[2],
        o = r[3],
        i = r[5];
    return (a <= 23 && n <= 59 && o <= 59 || 23 == a && 59 == n && 60 == o) && (!t || i)
}
bl.fast = {
    date: /^\d\d\d\d-[0-1]\d-[0-3]\d$/,
    time: /^(?:[0-2]\d:[0-5]\d:[0-5]\d|23:59:60)(?:\.\d+)?(?:z|[+-]\d\d(?::?\d\d)?)?$/i,
    "date-time": /^\d\d\d\d-[0-1]\d-[0-3]\d[t\s](?:[0-2]\d:[0-5]\d:[0-5]\d|23:59:60)(?:\.\d+)?(?:z|[+-]\d\d(?::?\d\d)?)$/i,
    uri: /^(?:[a-z][a-z0-9+\-.]*:)(?:\/?\/)?[^\s]*$/i,
    "uri-reference": /^(?:(?:[a-z][a-z0-9+\-.]*:)?\/?\/)?(?:[^\\\s#][^\s#]*)?(?:#[^\\\s]*)?$/i,
    "uri-template": hl,
    url: pl,
    email: /^[a-z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-z0-9](?:[a-z0-9-]{0,61}[a-z0-9])?(?:\.[a-z0-9](?:[a-z0-9-]{0,61}[a-z0-9])?)*$/i,
    hostname: ul,
    ipv4: /^(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?)$/,
    ipv6: /^\s*(?:(?:(?:[0-9a-f]{1,4}:){7}(?:[0-9a-f]{1,4}|:))|(?:(?:[0-9a-f]{1,4}:){6}(?::[0-9a-f]{1,4}|(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3})|:))|(?:(?:[0-9a-f]{1,4}:){5}(?:(?:(?::[0-9a-f]{1,4}){1,2})|:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3})|:))|(?:(?:[0-9a-f]{1,4}:){4}(?:(?:(?::[0-9a-f]{1,4}){1,3})|(?:(?::[0-9a-f]{1,4})?:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(?:(?:[0-9a-f]{1,4}:){3}(?:(?:(?::[0-9a-f]{1,4}){1,4})|(?:(?::[0-9a-f]{1,4}){0,2}:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(?:(?:[0-9a-f]{1,4}:){2}(?:(?:(?::[0-9a-f]{1,4}){1,5})|(?:(?::[0-9a-f]{1,4}){0,3}:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(?:(?:[0-9a-f]{1,4}:){1}(?:(?:(?::[0-9a-f]{1,4}){1,6})|(?:(?::[0-9a-f]{1,4}){0,4}:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(?::(?:(?:(?::[0-9a-f]{1,4}){1,7})|(?:(?::[0-9a-f]{1,4}){0,5}:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:)))(?:%.+)?\s*$/i,
    regex: Sl,
    uuid: fl,
    "json-pointer": ml,
    "json-pointer-uri-fragment": vl,
    "relative-json-pointer": gl
}, bl.full = {
    date: wl,
    time: El,
    "date-time": function(e) {
        var t = e.split(Pl);
        return 2 == t.length && wl(t[0]) && El(t[1], !0)
    },
    uri: function(e) {
        return kl.test(e) && dl.test(e)
    },
    "uri-reference": /^(?:[a-z][a-z0-9+\-.]*:)?(?:\/?\/(?:(?:[a-z0-9\-._~!$&'()*+,;=:]|%[0-9a-f]{2})*@)?(?:\[(?:(?:(?:(?:[0-9a-f]{1,4}:){6}|::(?:[0-9a-f]{1,4}:){5}|(?:[0-9a-f]{1,4})?::(?:[0-9a-f]{1,4}:){4}|(?:(?:[0-9a-f]{1,4}:){0,1}[0-9a-f]{1,4})?::(?:[0-9a-f]{1,4}:){3}|(?:(?:[0-9a-f]{1,4}:){0,2}[0-9a-f]{1,4})?::(?:[0-9a-f]{1,4}:){2}|(?:(?:[0-9a-f]{1,4}:){0,3}[0-9a-f]{1,4})?::[0-9a-f]{1,4}:|(?:(?:[0-9a-f]{1,4}:){0,4}[0-9a-f]{1,4})?::)(?:[0-9a-f]{1,4}:[0-9a-f]{1,4}|(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?))|(?:(?:[0-9a-f]{1,4}:){0,5}[0-9a-f]{1,4})?::[0-9a-f]{1,4}|(?:(?:[0-9a-f]{1,4}:){0,6}[0-9a-f]{1,4})?::)|[Vv][0-9a-f]+\.[a-z0-9\-._~!$&'()*+,;=:]+)\]|(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?)|(?:[a-z0-9\-._~!$&'"()*+,;=]|%[0-9a-f]{2})*)(?::\d*)?(?:\/(?:[a-z0-9\-._~!$&'"()*+,;=:@]|%[0-9a-f]{2})*)*|\/(?:(?:[a-z0-9\-._~!$&'"()*+,;=:@]|%[0-9a-f]{2})+(?:\/(?:[a-z0-9\-._~!$&'"()*+,;=:@]|%[0-9a-f]{2})*)*)?|(?:[a-z0-9\-._~!$&'"()*+,;=:@]|%[0-9a-f]{2})+(?:\/(?:[a-z0-9\-._~!$&'"()*+,;=:@]|%[0-9a-f]{2})*)*)?(?:\?(?:[a-z0-9\-._~!$&'"()*+,;=:@/?]|%[0-9a-f]{2})*)?(?:#(?:[a-z0-9\-._~!$&'"()*+,;=:@/?]|%[0-9a-f]{2})*)?$/i,
    "uri-template": hl,
    url: pl,
    email: /^[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?$/i,
    hostname: ul,
    ipv4: /^(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?)$/,
    ipv6: /^\s*(?:(?:(?:[0-9a-f]{1,4}:){7}(?:[0-9a-f]{1,4}|:))|(?:(?:[0-9a-f]{1,4}:){6}(?::[0-9a-f]{1,4}|(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3})|:))|(?:(?:[0-9a-f]{1,4}:){5}(?:(?:(?::[0-9a-f]{1,4}){1,2})|:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3})|:))|(?:(?:[0-9a-f]{1,4}:){4}(?:(?:(?::[0-9a-f]{1,4}){1,3})|(?:(?::[0-9a-f]{1,4})?:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(?:(?:[0-9a-f]{1,4}:){3}(?:(?:(?::[0-9a-f]{1,4}){1,4})|(?:(?::[0-9a-f]{1,4}){0,2}:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(?:(?:[0-9a-f]{1,4}:){2}(?:(?:(?::[0-9a-f]{1,4}){1,5})|(?:(?::[0-9a-f]{1,4}){0,3}:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(?:(?:[0-9a-f]{1,4}:){1}(?:(?:(?::[0-9a-f]{1,4}){1,6})|(?:(?::[0-9a-f]{1,4}){0,4}:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(?::(?:(?:(?::[0-9a-f]{1,4}){1,7})|(?:(?::[0-9a-f]{1,4}){0,5}:(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:)))(?:%.+)?\s*$/i,
    regex: Sl,
    uuid: fl,
    "json-pointer": ml,
    "json-pointer-uri-fragment": vl,
    "relative-json-pointer": gl
};
var Pl = /t|\s/i;
var kl = /\/|:/;
var _l = /[^\\]\\Z/;

function Sl(e) {
    if (_l.test(e)) return !1;
    try {
        return new RegExp(e), !0
    } catch (e) {
        return !1
    }
}
var Cl = function(e, t, r) {
        var a, n = " ",
            o = e.level,
            i = e.dataLevel,
            s = e.schema[t],
            l = e.schemaPath + e.util.getProperty(t),
            c = e.errSchemaPath + "/" + t,
            u = !e.opts.allErrors,
            d = "data" + (i || ""),
            h = e.opts.$data && s && s.$data;
        h ? (n += " var schema" + o + " = " + e.util.getData(s.$data, i, e.dataPathArr) + "; ", a = "schema" + o) : a = s;
        var p = "maximum" == t,
            f = p ? "exclusiveMaximum" : "exclusiveMinimum",
            m = e.schema[f],
            v = e.opts.$data && m && m.$data,
            g = p ? "<" : ">",
            y = p ? ">" : "<",
            b = void 0;
        if (!h && "number" != typeof s && void 0 !== s) throw new Error(t + " must be number");
        if (!v && void 0 !== m && "number" != typeof m && "boolean" != typeof m) throw new Error(f + " must be number or boolean");
        if (v) {
            var w = e.util.getData(m.$data, i, e.dataPathArr),
                E = "exclusive" + o,
                P = "exclType" + o,
                k = "exclIsNumber" + o,
                _ = "' + " + (T = "op" + o) + " + '";
            n += " var schemaExcl" + o + " = " + w + "; ", n += " var " + E + "; var " + P + " = typeof " + (w = "schemaExcl" + o) + "; if (" + P + " != 'boolean' && " + P + " != 'undefined' && " + P + " != 'number') { ";
            var S;
            b = f;
            (S = S || []).push(n), n = "", !1 !== e.createErrors ? (n += " { keyword: '" + (b || "_exclusiveLimit") + "' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: {} ", !1 !== e.opts.messages && (n += " , message: '" + f + " should be boolean' "), e.opts.verbose && (n += " , schema: validate.schema" + l + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), n += " } ") : n += " {} ";
            var C = n;
            n = S.pop(), !e.compositeRule && u ? e.async ? n += " throw new ValidationError([" + C + "]); " : n += " validate.errors = [" + C + "]; return false; " : n += " var err = " + C + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", n += " } else if ( ", h && (n += " (" + a + " !== undefined && typeof " + a + " != 'number') || "), n += " " + P + " == 'number' ? ( (" + E + " = " + a + " === undefined || " + w + " " + g + "= " + a + ") ? " + d + " " + y + "= " + w + " : " + d + " " + y + " " + a + " ) : ( (" + E + " = " + w + " === true) ? " + d + " " + y + "= " + a + " : " + d + " " + y + " " + a + " ) || " + d + " !== " + d + ") { var op" + o + " = " + E + " ? '" + g + "' : '" + g + "='; ", void 0 === s && (b = f, c = e.errSchemaPath + "/" + f, a = w, h = v)
        } else {
            _ = g;
            if ((k = "number" == typeof m) && h) {
                var T = "'" + _ + "'";
                n += " if ( ", h && (n += " (" + a + " !== undefined && typeof " + a + " != 'number') || "), n += " ( " + a + " === undefined || " + m + " " + g + "= " + a + " ? " + d + " " + y + "= " + m + " : " + d + " " + y + " " + a + " ) || " + d + " !== " + d + ") { "
            } else {
                k && void 0 === s ? (E = !0, b = f, c = e.errSchemaPath + "/" + f, a = m, y += "=") : (k && (a = Math[p ? "min" : "max"](m, s)), m === (!k || a) ? (E = !0, b = f, c = e.errSchemaPath + "/" + f, y += "=") : (E = !1, _ += "="));
                T = "'" + _ + "'";
                n += " if ( ", h && (n += " (" + a + " !== undefined && typeof " + a + " != 'number') || "), n += " " + d + " " + y + " " + a + " || " + d + " !== " + d + ") { "
            }
        }
        b = b || t, (S = S || []).push(n), n = "", !1 !== e.createErrors ? (n += " { keyword: '" + (b || "_limit") + "' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: { comparison: " + T + ", limit: " + a + ", exclusive: " + E + " } ", !1 !== e.opts.messages && (n += " , message: 'should be " + _ + " ", n += h ? "' + " + a : a + "'"), e.opts.verbose && (n += " , schema:  ", n += h ? "validate.schema" + l : "" + s, n += "         , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), n += " } ") : n += " {} ";
        C = n;
        return n = S.pop(), !e.compositeRule && u ? e.async ? n += " throw new ValidationError([" + C + "]); " : n += " validate.errors = [" + C + "]; return false; " : n += " var err = " + C + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", n += " } ", u && (n += " else { "), n
    },
    Tl = function(e, t, r) {
        var a, n = " ",
            o = e.level,
            i = e.dataLevel,
            s = e.schema[t],
            l = e.schemaPath + e.util.getProperty(t),
            c = e.errSchemaPath + "/" + t,
            u = !e.opts.allErrors,
            d = "data" + (i || ""),
            h = e.opts.$data && s && s.$data;
        if (h ? (n += " var schema" + o + " = " + e.util.getData(s.$data, i, e.dataPathArr) + "; ", a = "schema" + o) : a = s, !h && "number" != typeof s) throw new Error(t + " must be number");
        n += "if ( ", h && (n += " (" + a + " !== undefined && typeof " + a + " != 'number') || "), n += " " + d + ".length " + ("maxItems" == t ? ">" : "<") + " " + a + ") { ";
        var p = t,
            f = f || [];
        f.push(n), n = "", !1 !== e.createErrors ? (n += " { keyword: '" + (p || "_limitItems") + "' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: { limit: " + a + " } ", !1 !== e.opts.messages && (n += " , message: 'should NOT have ", n += "maxItems" == t ? "more" : "fewer", n += " than ", n += h ? "' + " + a + " + '" : "" + s, n += " items' "), e.opts.verbose && (n += " , schema:  ", n += h ? "validate.schema" + l : "" + s, n += "         , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), n += " } ") : n += " {} ";
        var m = n;
        return n = f.pop(), !e.compositeRule && u ? e.async ? n += " throw new ValidationError([" + m + "]); " : n += " validate.errors = [" + m + "]; return false; " : n += " var err = " + m + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", n += "} ", u && (n += " else { "), n
    },
    xl = function(e, t, r) {
        var a, n = " ",
            o = e.level,
            i = e.dataLevel,
            s = e.schema[t],
            l = e.schemaPath + e.util.getProperty(t),
            c = e.errSchemaPath + "/" + t,
            u = !e.opts.allErrors,
            d = "data" + (i || ""),
            h = e.opts.$data && s && s.$data;
        if (h ? (n += " var schema" + o + " = " + e.util.getData(s.$data, i, e.dataPathArr) + "; ", a = "schema" + o) : a = s, !h && "number" != typeof s) throw new Error(t + " must be number");
        var p = "maxLength" == t ? ">" : "<";
        n += "if ( ", h && (n += " (" + a + " !== undefined && typeof " + a + " != 'number') || "), !1 === e.opts.unicode ? n += " " + d + ".length " : n += " ucs2length(" + d + ") ", n += " " + p + " " + a + ") { ";
        var f = t,
            m = m || [];
        m.push(n), n = "", !1 !== e.createErrors ? (n += " { keyword: '" + (f || "_limitLength") + "' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: { limit: " + a + " } ", !1 !== e.opts.messages && (n += " , message: 'should NOT be ", n += "maxLength" == t ? "longer" : "shorter", n += " than ", n += h ? "' + " + a + " + '" : "" + s, n += " characters' "), e.opts.verbose && (n += " , schema:  ", n += h ? "validate.schema" + l : "" + s, n += "         , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), n += " } ") : n += " {} ";
        var v = n;
        return n = m.pop(), !e.compositeRule && u ? e.async ? n += " throw new ValidationError([" + v + "]); " : n += " validate.errors = [" + v + "]; return false; " : n += " var err = " + v + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", n += "} ", u && (n += " else { "), n
    },
    Dl = function(e, t, r) {
        var a, n = " ",
            o = e.level,
            i = e.dataLevel,
            s = e.schema[t],
            l = e.schemaPath + e.util.getProperty(t),
            c = e.errSchemaPath + "/" + t,
            u = !e.opts.allErrors,
            d = "data" + (i || ""),
            h = e.opts.$data && s && s.$data;
        if (h ? (n += " var schema" + o + " = " + e.util.getData(s.$data, i, e.dataPathArr) + "; ", a = "schema" + o) : a = s, !h && "number" != typeof s) throw new Error(t + " must be number");
        n += "if ( ", h && (n += " (" + a + " !== undefined && typeof " + a + " != 'number') || "), n += " Object.keys(" + d + ").length " + ("maxProperties" == t ? ">" : "<") + " " + a + ") { ";
        var p = t,
            f = f || [];
        f.push(n), n = "", !1 !== e.createErrors ? (n += " { keyword: '" + (p || "_limitProperties") + "' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: { limit: " + a + " } ", !1 !== e.opts.messages && (n += " , message: 'should NOT have ", n += "maxProperties" == t ? "more" : "fewer", n += " than ", n += h ? "' + " + a + " + '" : "" + s, n += " properties' "), e.opts.verbose && (n += " , schema:  ", n += h ? "validate.schema" + l : "" + s, n += "         , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), n += " } ") : n += " {} ";
        var m = n;
        return n = f.pop(), !e.compositeRule && u ? e.async ? n += " throw new ValidationError([" + m + "]); " : n += " validate.errors = [" + m + "]; return false; " : n += " var err = " + m + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", n += "} ", u && (n += " else { "), n
    },
    Ol = {
        $ref: function(e, t, r) {
            var a, n, o = " ",
                i = e.level,
                s = e.dataLevel,
                l = e.schema[t],
                c = e.errSchemaPath + "/" + t,
                u = !e.opts.allErrors,
                d = "data" + (s || ""),
                h = "valid" + i;
            if ("#" == l || "#/" == l) e.isRoot ? (a = e.async, n = "validate") : (a = !0 === e.root.schema.$async, n = "root.refVal[0]");
            else {
                var p = e.resolveRef(e.baseId, l, e.isRoot);
                if (void 0 === p) {
                    var f = e.MissingRefError.message(e.baseId, l);
                    if ("fail" == e.opts.missingRefs) {
                        e.logger.error(f), (y = y || []).push(o), o = "", !1 !== e.createErrors ? (o += " { keyword: '$ref' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: { ref: '" + e.util.escapeQuotes(l) + "' } ", !1 !== e.opts.messages && (o += " , message: 'can\\'t resolve reference " + e.util.escapeQuotes(l) + "' "), e.opts.verbose && (o += " , schema: " + e.util.toQuotedString(l) + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), o += " } ") : o += " {} ";
                        var m = o;
                        o = y.pop(), !e.compositeRule && u ? e.async ? o += " throw new ValidationError([" + m + "]); " : o += " validate.errors = [" + m + "]; return false; " : o += " var err = " + m + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", u && (o += " if (false) { ")
                    } else {
                        if ("ignore" != e.opts.missingRefs) throw new e.MissingRefError(e.baseId, l, f);
                        e.logger.warn(f), u && (o += " if (true) { ")
                    }
                } else if (p.inline) {
                    var v = e.util.copy(e);
                    v.level++;
                    var g = "valid" + v.level;
                    v.schema = p.schema, v.schemaPath = "", v.errSchemaPath = l, o += " " + e.validate(v).replace(/validate\.schema/g, p.code) + " ", u && (o += " if (" + g + ") { ")
                } else a = !0 === p.$async || e.async && !1 !== p.$async, n = p.code
            }
            if (n) {
                var y;
                (y = y || []).push(o), o = "", e.opts.passContext ? o += " " + n + ".call(this, " : o += " " + n + "( ", o += " " + d + ", (dataPath || '')", '""' != e.errorPath && (o += " + " + e.errorPath);
                var b = o += " , " + (s ? "data" + (s - 1 || "") : "parentData") + " , " + (s ? e.dataPathArr[s] : "parentDataProperty") + ", rootData)  ";
                if (o = y.pop(), a) {
                    if (!e.async) throw new Error("async schema referenced by sync schema");
                    u && (o += " var " + h + "; "), o += " try { await " + b + "; ", u && (o += " " + h + " = true; "), o += " } catch (e) { if (!(e instanceof ValidationError)) throw e; if (vErrors === null) vErrors = e.errors; else vErrors = vErrors.concat(e.errors); errors = vErrors.length; ", u && (o += " " + h + " = false; "), o += " } ", u && (o += " if (" + h + ") { ")
                } else o += " if (!" + b + ") { if (vErrors === null) vErrors = " + n + ".errors; else vErrors = vErrors.concat(" + n + ".errors); errors = vErrors.length; } ", u && (o += " else { ")
            }
            return o
        },
        allOf: function(e, t, r) {
            var a = " ",
                n = e.schema[t],
                o = e.schemaPath + e.util.getProperty(t),
                i = e.errSchemaPath + "/" + t,
                s = !e.opts.allErrors,
                l = e.util.copy(e),
                c = "";
            l.level++;
            var u = "valid" + l.level,
                d = l.baseId,
                h = !0,
                p = n;
            if (p)
                for (var f, m = -1, v = p.length - 1; m < v;) f = p[m += 1], (e.opts.strictKeywords ? "object" == typeof f && Object.keys(f).length > 0 || !1 === f : e.util.schemaHasRules(f, e.RULES.all)) && (h = !1, l.schema = f, l.schemaPath = o + "[" + m + "]", l.errSchemaPath = i + "/" + m, a += "  " + e.validate(l) + " ", l.baseId = d, s && (a += " if (" + u + ") { ", c += "}"));
            return s && (a += h ? " if (true) { " : " " + c.slice(0, -1) + " "), a
        },
        anyOf: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "valid" + n,
                h = "errs__" + n,
                p = e.util.copy(e),
                f = "";
            p.level++;
            var m = "valid" + p.level;
            if (i.every((function(t) {
                    return e.opts.strictKeywords ? "object" == typeof t && Object.keys(t).length > 0 || !1 === t : e.util.schemaHasRules(t, e.RULES.all)
                }))) {
                var v = p.baseId;
                a += " var " + h + " = errors; var " + d + " = false;  ";
                var g = e.compositeRule;
                e.compositeRule = p.compositeRule = !0;
                var y = i;
                if (y)
                    for (var b, w = -1, E = y.length - 1; w < E;) b = y[w += 1], p.schema = b, p.schemaPath = s + "[" + w + "]", p.errSchemaPath = l + "/" + w, a += "  " + e.validate(p) + " ", p.baseId = v, a += " " + d + " = " + d + " || " + m + "; if (!" + d + ") { ", f += "}";
                e.compositeRule = p.compositeRule = g, a += " " + f + " if (!" + d + ") {   var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'anyOf' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: {} ", !1 !== e.opts.messages && (a += " , message: 'should match some schema in anyOf' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", !e.compositeRule && c && (e.async ? a += " throw new ValidationError(vErrors); " : a += " validate.errors = vErrors; return false; "), a += " } else {  errors = " + h + "; if (vErrors !== null) { if (" + h + ") vErrors.length = " + h + "; else vErrors = null; } ", e.opts.allErrors && (a += " } ")
            } else c && (a += " if (true) { ");
            return a
        },
        $comment: function(e, t, r) {
            var a = " ",
                n = e.schema[t],
                o = e.errSchemaPath + "/" + t,
                i = (e.opts.allErrors, e.util.toQuotedString(n));
            return !0 === e.opts.$comment ? a += " console.log(" + i + ");" : "function" == typeof e.opts.$comment && (a += " self._opts.$comment(" + i + ", " + e.util.toQuotedString(o) + ", validate.root.schema);"), a
        },
        const: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "valid" + n,
                h = e.opts.$data && i && i.$data;
            h && (a += " var schema" + n + " = " + e.util.getData(i.$data, o, e.dataPathArr) + "; "), h || (a += " var schema" + n + " = validate.schema" + s + ";"), a += "var " + d + " = equal(" + u + ", schema" + n + "); if (!" + d + ") {   ";
            var p = p || [];
            p.push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'const' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { allowedValue: schema" + n + " } ", !1 !== e.opts.messages && (a += " , message: 'should be equal to constant' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
            var f = a;
            return a = p.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + f + "]); " : a += " validate.errors = [" + f + "]; return false; " : a += " var err = " + f + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " }", c && (a += " else { "), a
        },
        contains: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "valid" + n,
                h = "errs__" + n,
                p = e.util.copy(e);
            p.level++;
            var f = "valid" + p.level,
                m = "i" + n,
                v = p.dataLevel = e.dataLevel + 1,
                g = "data" + v,
                y = e.baseId,
                b = e.opts.strictKeywords ? "object" == typeof i && Object.keys(i).length > 0 || !1 === i : e.util.schemaHasRules(i, e.RULES.all);
            if (a += "var " + h + " = errors;var " + d + ";", b) {
                var w = e.compositeRule;
                e.compositeRule = p.compositeRule = !0, p.schema = i, p.schemaPath = s, p.errSchemaPath = l, a += " var " + f + " = false; for (var " + m + " = 0; " + m + " < " + u + ".length; " + m + "++) { ", p.errorPath = e.util.getPathExpr(e.errorPath, m, e.opts.jsonPointers, !0);
                var E = u + "[" + m + "]";
                p.dataPathArr[v] = m;
                var P = e.validate(p);
                p.baseId = y, e.util.varOccurences(P, g) < 2 ? a += " " + e.util.varReplace(P, g, E) + " " : a += " var " + g + " = " + E + "; " + P + " ", a += " if (" + f + ") break; }  ", e.compositeRule = p.compositeRule = w, a += "  if (!" + f + ") {"
            } else a += " if (" + u + ".length == 0) {";
            var k = k || [];
            k.push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'contains' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: {} ", !1 !== e.opts.messages && (a += " , message: 'should contain a valid item' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
            var _ = a;
            return a = k.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + _ + "]); " : a += " validate.errors = [" + _ + "]; return false; " : a += " var err = " + _ + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " } else { ", b && (a += "  errors = " + h + "; if (vErrors !== null) { if (" + h + ") vErrors.length = " + h + "; else vErrors = null; } "), e.opts.allErrors && (a += " } "), a
        },
        dependencies: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "errs__" + n,
                h = e.util.copy(e),
                p = "";
            h.level++;
            var f = "valid" + h.level,
                m = {},
                v = {},
                g = e.opts.ownProperties;
            for (E in i)
                if ("__proto__" != E) {
                    var y = i[E],
                        b = Array.isArray(y) ? v : m;
                    b[E] = y
                } a += "var " + d + " = errors;";
            var w = e.errorPath;
            for (var E in a += "var missing" + n + ";", v)
                if ((b = v[E]).length) {
                    if (a += " if ( " + u + e.util.getProperty(E) + " !== undefined ", g && (a += " && Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(E) + "') "), c) {
                        a += " && ( ";
                        var P = b;
                        if (P)
                            for (var k = -1, _ = P.length - 1; k < _;) {
                                O = P[k += 1], k && (a += " || "), a += " ( ( " + (A = u + ($ = e.util.getProperty(O))) + " === undefined ", g && (a += " || ! Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(O) + "') "), a += ") && (missing" + n + " = " + e.util.toQuotedString(e.opts.jsonPointers ? O : $) + ") ) "
                            }
                        a += ")) {  ";
                        var S = "missing" + n,
                            C = "' + " + S + " + '";
                        e.opts._errorDataPathProperty && (e.errorPath = e.opts.jsonPointers ? e.util.getPathExpr(w, S, !0) : w + " + " + S);
                        var T = T || [];
                        T.push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'dependencies' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { property: '" + e.util.escapeQuotes(E) + "', missingProperty: '" + C + "', depsCount: " + b.length + ", deps: '" + e.util.escapeQuotes(1 == b.length ? b[0] : b.join(", ")) + "' } ", !1 !== e.opts.messages && (a += " , message: 'should have ", 1 == b.length ? a += "property " + e.util.escapeQuotes(b[0]) : a += "properties " + e.util.escapeQuotes(b.join(", ")), a += " when property " + e.util.escapeQuotes(E) + " is present' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
                        var x = a;
                        a = T.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + x + "]); " : a += " validate.errors = [" + x + "]; return false; " : a += " var err = " + x + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; "
                    } else {
                        a += " ) { ";
                        var D = b;
                        if (D)
                            for (var O, R = -1, F = D.length - 1; R < F;) {
                                O = D[R += 1];
                                var $ = e.util.getProperty(O),
                                    A = (C = e.util.escapeQuotes(O), u + $);
                                e.opts._errorDataPathProperty && (e.errorPath = e.util.getPath(w, O, e.opts.jsonPointers)), a += " if ( " + A + " === undefined ", g && (a += " || ! Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(O) + "') "), a += ") {  var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'dependencies' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { property: '" + e.util.escapeQuotes(E) + "', missingProperty: '" + C + "', depsCount: " + b.length + ", deps: '" + e.util.escapeQuotes(1 == b.length ? b[0] : b.join(", ")) + "' } ", !1 !== e.opts.messages && (a += " , message: 'should have ", 1 == b.length ? a += "property " + e.util.escapeQuotes(b[0]) : a += "properties " + e.util.escapeQuotes(b.join(", ")), a += " when property " + e.util.escapeQuotes(E) + " is present' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; } "
                            }
                    }
                    a += " }   ", c && (p += "}", a += " else { ")
                } e.errorPath = w;
            var M = h.baseId;
            for (var E in m) {
                y = m[E];
                (e.opts.strictKeywords ? "object" == typeof y && Object.keys(y).length > 0 || !1 === y : e.util.schemaHasRules(y, e.RULES.all)) && (a += " " + f + " = true; if ( " + u + e.util.getProperty(E) + " !== undefined ", g && (a += " && Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(E) + "') "), a += ") { ", h.schema = y, h.schemaPath = s + e.util.getProperty(E), h.errSchemaPath = l + "/" + e.util.escapeFragment(E), a += "  " + e.validate(h) + " ", h.baseId = M, a += " }  ", c && (a += " if (" + f + ") { ", p += "}"))
            }
            return c && (a += "   " + p + " if (" + d + " == errors) {"), a
        },
        enum: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "valid" + n,
                h = e.opts.$data && i && i.$data;
            h && (a += " var schema" + n + " = " + e.util.getData(i.$data, o, e.dataPathArr) + "; ");
            var p = "i" + n,
                f = "schema" + n;
            h || (a += " var " + f + " = validate.schema" + s + ";"), a += "var " + d + ";", h && (a += " if (schema" + n + " === undefined) " + d + " = true; else if (!Array.isArray(schema" + n + ")) " + d + " = false; else {"), a += d + " = false;for (var " + p + "=0; " + p + "<" + f + ".length; " + p + "++) if (equal(" + u + ", " + f + "[" + p + "])) { " + d + " = true; break; }", h && (a += "  }  "), a += " if (!" + d + ") {   ";
            var m = m || [];
            m.push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'enum' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { allowedValues: schema" + n + " } ", !1 !== e.opts.messages && (a += " , message: 'should be equal to one of the allowed values' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
            var v = a;
            return a = m.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + v + "]); " : a += " validate.errors = [" + v + "]; return false; " : a += " var err = " + v + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " }", c && (a += " else { "), a
        },
        format: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || "");
            if (!1 === e.opts.format) return c && (a += " if (true) { "), a;
            var d, h = e.opts.$data && i && i.$data;
            h ? (a += " var schema" + n + " = " + e.util.getData(i.$data, o, e.dataPathArr) + "; ", d = "schema" + n) : d = i;
            var p = e.opts.unknownFormats,
                f = Array.isArray(p);
            if (h) {
                a += " var " + (m = "format" + n) + " = formats[" + d + "]; var " + (v = "isObject" + n) + " = typeof " + m + " == 'object' && !(" + m + " instanceof RegExp) && " + m + ".validate; var " + (g = "formatType" + n) + " = " + v + " && " + m + ".type || 'string'; if (" + v + ") { ", e.async && (a += " var async" + n + " = " + m + ".async; "), a += " " + m + " = " + m + ".validate; } if (  ", h && (a += " (" + d + " !== undefined && typeof " + d + " != 'string') || "), a += " (", "ignore" != p && (a += " (" + d + " && !" + m + " ", f && (a += " && self._opts.unknownFormats.indexOf(" + d + ") == -1 "), a += ") || "), a += " (" + m + " && " + g + " == '" + r + "' && !(typeof " + m + " == 'function' ? ", e.async ? a += " (async" + n + " ? await " + m + "(" + u + ") : " + m + "(" + u + ")) " : a += " " + m + "(" + u + ") ", a += " : " + m + ".test(" + u + "))))) {"
            } else {
                var m;
                if (!(m = e.formats[i])) {
                    if ("ignore" == p) return e.logger.warn('unknown format "' + i + '" ignored in schema at path "' + e.errSchemaPath + '"'), c && (a += " if (true) { "), a;
                    if (f && p.indexOf(i) >= 0) return c && (a += " if (true) { "), a;
                    throw new Error('unknown format "' + i + '" is used in schema at path "' + e.errSchemaPath + '"')
                }
                var v, g = (v = "object" == typeof m && !(m instanceof RegExp) && m.validate) && m.type || "string";
                if (v) {
                    var y = !0 === m.async;
                    m = m.validate
                }
                if (g != r) return c && (a += " if (true) { "), a;
                if (y) {
                    if (!e.async) throw new Error("async format in sync schema");
                    a += " if (!(await " + (b = "formats" + e.util.getProperty(i) + ".validate") + "(" + u + "))) { "
                } else {
                    a += " if (! ";
                    var b = "formats" + e.util.getProperty(i);
                    v && (b += ".validate"), a += "function" == typeof m ? " " + b + "(" + u + ") " : " " + b + ".test(" + u + ") ", a += ") { "
                }
            }
            var w = w || [];
            w.push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'format' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { format:  ", a += h ? "" + d : "" + e.util.toQuotedString(i), a += "  } ", !1 !== e.opts.messages && (a += " , message: 'should match format \"", a += h ? "' + " + d + " + '" : "" + e.util.escapeQuotes(i), a += "\"' "), e.opts.verbose && (a += " , schema:  ", a += h ? "validate.schema" + s : "" + e.util.toQuotedString(i), a += "         , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
            var E = a;
            return a = w.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + E + "]); " : a += " validate.errors = [" + E + "]; return false; " : a += " var err = " + E + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " } ", c && (a += " else { "), a
        },
        if: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "valid" + n,
                h = "errs__" + n,
                p = e.util.copy(e);
            p.level++;
            var f = "valid" + p.level,
                m = e.schema.then,
                v = e.schema.else,
                g = void 0 !== m && (e.opts.strictKeywords ? "object" == typeof m && Object.keys(m).length > 0 || !1 === m : e.util.schemaHasRules(m, e.RULES.all)),
                y = void 0 !== v && (e.opts.strictKeywords ? "object" == typeof v && Object.keys(v).length > 0 || !1 === v : e.util.schemaHasRules(v, e.RULES.all)),
                b = p.baseId;
            if (g || y) {
                var w;
                p.createErrors = !1, p.schema = i, p.schemaPath = s, p.errSchemaPath = l, a += " var " + h + " = errors; var " + d + " = true;  ";
                var E = e.compositeRule;
                e.compositeRule = p.compositeRule = !0, a += "  " + e.validate(p) + " ", p.baseId = b, p.createErrors = !0, a += "  errors = " + h + "; if (vErrors !== null) { if (" + h + ") vErrors.length = " + h + "; else vErrors = null; }  ", e.compositeRule = p.compositeRule = E, g ? (a += " if (" + f + ") {  ", p.schema = e.schema.then, p.schemaPath = e.schemaPath + ".then", p.errSchemaPath = e.errSchemaPath + "/then", a += "  " + e.validate(p) + " ", p.baseId = b, a += " " + d + " = " + f + "; ", g && y ? a += " var " + (w = "ifClause" + n) + " = 'then'; " : w = "'then'", a += " } ", y && (a += " else { ")) : a += " if (!" + f + ") { ", y && (p.schema = e.schema.else, p.schemaPath = e.schemaPath + ".else", p.errSchemaPath = e.errSchemaPath + "/else", a += "  " + e.validate(p) + " ", p.baseId = b, a += " " + d + " = " + f + "; ", g && y ? a += " var " + (w = "ifClause" + n) + " = 'else'; " : w = "'else'", a += " } "), a += " if (!" + d + ") {   var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'if' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { failingKeyword: " + w + " } ", !1 !== e.opts.messages && (a += " , message: 'should match \"' + " + w + " + '\" schema' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", !e.compositeRule && c && (e.async ? a += " throw new ValidationError(vErrors); " : a += " validate.errors = vErrors; return false; "), a += " }   ", c && (a += " else { ")
            } else c && (a += " if (true) { ");
            return a
        },
        items: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "valid" + n,
                h = "errs__" + n,
                p = e.util.copy(e),
                f = "";
            p.level++;
            var m = "valid" + p.level,
                v = "i" + n,
                g = p.dataLevel = e.dataLevel + 1,
                y = "data" + g,
                b = e.baseId;
            if (a += "var " + h + " = errors;var " + d + ";", Array.isArray(i)) {
                var w = e.schema.additionalItems;
                if (!1 === w) {
                    a += " " + d + " = " + u + ".length <= " + i.length + "; ";
                    var E = l;
                    l = e.errSchemaPath + "/additionalItems", a += "  if (!" + d + ") {   ";
                    var P = P || [];
                    P.push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'additionalItems' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { limit: " + i.length + " } ", !1 !== e.opts.messages && (a += " , message: 'should NOT have more than " + i.length + " items' "), e.opts.verbose && (a += " , schema: false , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
                    var k = a;
                    a = P.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + k + "]); " : a += " validate.errors = [" + k + "]; return false; " : a += " var err = " + k + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " } ", l = E, c && (f += "}", a += " else { ")
                }
                var _ = i;
                if (_)
                    for (var S, C = -1, T = _.length - 1; C < T;)
                        if (S = _[C += 1], e.opts.strictKeywords ? "object" == typeof S && Object.keys(S).length > 0 || !1 === S : e.util.schemaHasRules(S, e.RULES.all)) {
                            a += " " + m + " = true; if (" + u + ".length > " + C + ") { ";
                            var x = u + "[" + C + "]";
                            p.schema = S, p.schemaPath = s + "[" + C + "]", p.errSchemaPath = l + "/" + C, p.errorPath = e.util.getPathExpr(e.errorPath, C, e.opts.jsonPointers, !0), p.dataPathArr[g] = C;
                            var D = e.validate(p);
                            p.baseId = b, e.util.varOccurences(D, y) < 2 ? a += " " + e.util.varReplace(D, y, x) + " " : a += " var " + y + " = " + x + "; " + D + " ", a += " }  ", c && (a += " if (" + m + ") { ", f += "}")
                        } if ("object" == typeof w && (e.opts.strictKeywords ? "object" == typeof w && Object.keys(w).length > 0 || !1 === w : e.util.schemaHasRules(w, e.RULES.all))) {
                    p.schema = w, p.schemaPath = e.schemaPath + ".additionalItems", p.errSchemaPath = e.errSchemaPath + "/additionalItems", a += " " + m + " = true; if (" + u + ".length > " + i.length + ") {  for (var " + v + " = " + i.length + "; " + v + " < " + u + ".length; " + v + "++) { ", p.errorPath = e.util.getPathExpr(e.errorPath, v, e.opts.jsonPointers, !0);
                    x = u + "[" + v + "]";
                    p.dataPathArr[g] = v;
                    D = e.validate(p);
                    p.baseId = b, e.util.varOccurences(D, y) < 2 ? a += " " + e.util.varReplace(D, y, x) + " " : a += " var " + y + " = " + x + "; " + D + " ", c && (a += " if (!" + m + ") break; "), a += " } }  ", c && (a += " if (" + m + ") { ", f += "}")
                }
            } else if (e.opts.strictKeywords ? "object" == typeof i && Object.keys(i).length > 0 || !1 === i : e.util.schemaHasRules(i, e.RULES.all)) {
                p.schema = i, p.schemaPath = s, p.errSchemaPath = l, a += "  for (var " + v + " = 0; " + v + " < " + u + ".length; " + v + "++) { ", p.errorPath = e.util.getPathExpr(e.errorPath, v, e.opts.jsonPointers, !0);
                x = u + "[" + v + "]";
                p.dataPathArr[g] = v;
                D = e.validate(p);
                p.baseId = b, e.util.varOccurences(D, y) < 2 ? a += " " + e.util.varReplace(D, y, x) + " " : a += " var " + y + " = " + x + "; " + D + " ", c && (a += " if (!" + m + ") break; "), a += " }"
            }
            return c && (a += " " + f + " if (" + h + " == errors) {"), a
        },
        maximum: Cl,
        minimum: Cl,
        maxItems: Tl,
        minItems: Tl,
        maxLength: xl,
        minLength: xl,
        maxProperties: Dl,
        minProperties: Dl,
        multipleOf: function(e, t, r) {
            var a, n = " ",
                o = e.level,
                i = e.dataLevel,
                s = e.schema[t],
                l = e.schemaPath + e.util.getProperty(t),
                c = e.errSchemaPath + "/" + t,
                u = !e.opts.allErrors,
                d = "data" + (i || ""),
                h = e.opts.$data && s && s.$data;
            if (h ? (n += " var schema" + o + " = " + e.util.getData(s.$data, i, e.dataPathArr) + "; ", a = "schema" + o) : a = s, !h && "number" != typeof s) throw new Error(t + " must be number");
            n += "var division" + o + ";if (", h && (n += " " + a + " !== undefined && ( typeof " + a + " != 'number' || "), n += " (division" + o + " = " + d + " / " + a + ", ", e.opts.multipleOfPrecision ? n += " Math.abs(Math.round(division" + o + ") - division" + o + ") > 1e-" + e.opts.multipleOfPrecision + " " : n += " division" + o + " !== parseInt(division" + o + ") ", n += " ) ", h && (n += "  )  "), n += " ) {   ";
            var p = p || [];
            p.push(n), n = "", !1 !== e.createErrors ? (n += " { keyword: 'multipleOf' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: { multipleOf: " + a + " } ", !1 !== e.opts.messages && (n += " , message: 'should be multiple of ", n += h ? "' + " + a : a + "'"), e.opts.verbose && (n += " , schema:  ", n += h ? "validate.schema" + l : "" + s, n += "         , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), n += " } ") : n += " {} ";
            var f = n;
            return n = p.pop(), !e.compositeRule && u ? e.async ? n += " throw new ValidationError([" + f + "]); " : n += " validate.errors = [" + f + "]; return false; " : n += " var err = " + f + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", n += "} ", u && (n += " else { "), n
        },
        not: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "errs__" + n,
                h = e.util.copy(e);
            h.level++;
            var p = "valid" + h.level;
            if (e.opts.strictKeywords ? "object" == typeof i && Object.keys(i).length > 0 || !1 === i : e.util.schemaHasRules(i, e.RULES.all)) {
                h.schema = i, h.schemaPath = s, h.errSchemaPath = l, a += " var " + d + " = errors;  ";
                var f, m = e.compositeRule;
                e.compositeRule = h.compositeRule = !0, h.createErrors = !1, h.opts.allErrors && (f = h.opts.allErrors, h.opts.allErrors = !1), a += " " + e.validate(h) + " ", h.createErrors = !0, f && (h.opts.allErrors = f), e.compositeRule = h.compositeRule = m, a += " if (" + p + ") {   ";
                var v = v || [];
                v.push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'not' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: {} ", !1 !== e.opts.messages && (a += " , message: 'should NOT be valid' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
                var g = a;
                a = v.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + g + "]); " : a += " validate.errors = [" + g + "]; return false; " : a += " var err = " + g + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " } else {  errors = " + d + "; if (vErrors !== null) { if (" + d + ") vErrors.length = " + d + "; else vErrors = null; } ", e.opts.allErrors && (a += " } ")
            } else a += "  var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'not' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: {} ", !1 !== e.opts.messages && (a += " , message: 'should NOT be valid' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", c && (a += " if (false) { ");
            return a
        },
        oneOf: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "valid" + n,
                h = "errs__" + n,
                p = e.util.copy(e),
                f = "";
            p.level++;
            var m = "valid" + p.level,
                v = p.baseId,
                g = "prevValid" + n,
                y = "passingSchemas" + n;
            a += "var " + h + " = errors , " + g + " = false , " + d + " = false , " + y + " = null; ";
            var b = e.compositeRule;
            e.compositeRule = p.compositeRule = !0;
            var w = i;
            if (w)
                for (var E, P = -1, k = w.length - 1; P < k;) E = w[P += 1], (e.opts.strictKeywords ? "object" == typeof E && Object.keys(E).length > 0 || !1 === E : e.util.schemaHasRules(E, e.RULES.all)) ? (p.schema = E, p.schemaPath = s + "[" + P + "]", p.errSchemaPath = l + "/" + P, a += "  " + e.validate(p) + " ", p.baseId = v) : a += " var " + m + " = true; ", P && (a += " if (" + m + " && " + g + ") { " + d + " = false; " + y + " = [" + y + ", " + P + "]; } else { ", f += "}"), a += " if (" + m + ") { " + d + " = " + g + " = true; " + y + " = " + P + "; }";
            return e.compositeRule = p.compositeRule = b, a += f + "if (!" + d + ") {   var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'oneOf' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { passingSchemas: " + y + " } ", !1 !== e.opts.messages && (a += " , message: 'should match exactly one schema in oneOf' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", !e.compositeRule && c && (e.async ? a += " throw new ValidationError(vErrors); " : a += " validate.errors = vErrors; return false; "), a += "} else {  errors = " + h + "; if (vErrors !== null) { if (" + h + ") vErrors.length = " + h + "; else vErrors = null; }", e.opts.allErrors && (a += " } "), a
        },
        pattern: function(e, t, r) {
            var a, n = " ",
                o = e.level,
                i = e.dataLevel,
                s = e.schema[t],
                l = e.schemaPath + e.util.getProperty(t),
                c = e.errSchemaPath + "/" + t,
                u = !e.opts.allErrors,
                d = "data" + (i || ""),
                h = e.opts.$data && s && s.$data;
            h ? (n += " var schema" + o + " = " + e.util.getData(s.$data, i, e.dataPathArr) + "; ", a = "schema" + o) : a = s, n += "if ( ", h && (n += " (" + a + " !== undefined && typeof " + a + " != 'string') || "), n += " !" + (h ? "(new RegExp(" + a + "))" : e.usePattern(s)) + ".test(" + d + ") ) {   ";
            var p = p || [];
            p.push(n), n = "", !1 !== e.createErrors ? (n += " { keyword: 'pattern' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: { pattern:  ", n += h ? "" + a : "" + e.util.toQuotedString(s), n += "  } ", !1 !== e.opts.messages && (n += " , message: 'should match pattern \"", n += h ? "' + " + a + " + '" : "" + e.util.escapeQuotes(s), n += "\"' "), e.opts.verbose && (n += " , schema:  ", n += h ? "validate.schema" + l : "" + e.util.toQuotedString(s), n += "         , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), n += " } ") : n += " {} ";
            var f = n;
            return n = p.pop(), !e.compositeRule && u ? e.async ? n += " throw new ValidationError([" + f + "]); " : n += " validate.errors = [" + f + "]; return false; " : n += " var err = " + f + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", n += "} ", u && (n += " else { "), n
        },
        properties: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "errs__" + n,
                h = e.util.copy(e),
                p = "";
            h.level++;
            var f = "valid" + h.level,
                m = "key" + n,
                v = "idx" + n,
                g = h.dataLevel = e.dataLevel + 1,
                y = "data" + g,
                b = "dataProperties" + n,
                w = Object.keys(i || {}).filter($),
                E = e.schema.patternProperties || {},
                P = Object.keys(E).filter($),
                k = e.schema.additionalProperties,
                _ = w.length || P.length,
                S = !1 === k,
                C = "object" == typeof k && Object.keys(k).length,
                T = e.opts.removeAdditional,
                x = S || C || T,
                D = e.opts.ownProperties,
                O = e.baseId,
                R = e.schema.required;
            if (R && (!e.opts.$data || !R.$data) && R.length < e.opts.loopRequired) var F = e.util.toHash(R);

            function $(e) {
                return "__proto__" !== e
            }
            if (a += "var " + d + " = errors;var " + f + " = true;", D && (a += " var " + b + " = undefined;"), x) {
                if (a += D ? " " + b + " = " + b + " || Object.keys(" + u + "); for (var " + v + "=0; " + v + "<" + b + ".length; " + v + "++) { var " + m + " = " + b + "[" + v + "]; " : " for (var " + m + " in " + u + ") { ", _) {
                    if (a += " var isAdditional" + n + " = !(false ", w.length)
                        if (w.length > 8) a += " || validate.schema" + s + ".hasOwnProperty(" + m + ") ";
                        else {
                            var A = w;
                            if (A)
                                for (var M = -1, L = A.length - 1; M < L;) Q = A[M += 1], a += " || " + m + " == " + e.util.toQuotedString(Q) + " "
                        } if (P.length) {
                        var N = P;
                        if (N)
                            for (var I = -1, j = N.length - 1; I < j;) oe = N[I += 1], a += " || " + e.usePattern(oe) + ".test(" + m + ") "
                    }
                    a += " ); if (isAdditional" + n + ") { "
                }
                if ("all" == T) a += " delete " + u + "[" + m + "]; ";
                else {
                    var U = e.errorPath,
                        H = "' + " + m + " + '";
                    if (e.opts._errorDataPathProperty && (e.errorPath = e.util.getPathExpr(e.errorPath, m, e.opts.jsonPointers)), S)
                        if (T) a += " delete " + u + "[" + m + "]; ";
                        else {
                            a += " " + f + " = false; ";
                            var q = l;
                            l = e.errSchemaPath + "/additionalProperties", (re = re || []).push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'additionalProperties' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { additionalProperty: '" + H + "' } ", !1 !== e.opts.messages && (a += " , message: '", e.opts._errorDataPathProperty ? a += "is an invalid additional property" : a += "should NOT have additional properties", a += "' "), e.opts.verbose && (a += " , schema: false , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
                            var Y = a;
                            a = re.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + Y + "]); " : a += " validate.errors = [" + Y + "]; return false; " : a += " var err = " + Y + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", l = q, c && (a += " break; ")
                        }
                    else if (C)
                        if ("failing" == T) {
                            a += " var " + d + " = errors;  ";
                            var B = e.compositeRule;
                            e.compositeRule = h.compositeRule = !0, h.schema = k, h.schemaPath = e.schemaPath + ".additionalProperties", h.errSchemaPath = e.errSchemaPath + "/additionalProperties", h.errorPath = e.opts._errorDataPathProperty ? e.errorPath : e.util.getPathExpr(e.errorPath, m, e.opts.jsonPointers);
                            var W = u + "[" + m + "]";
                            h.dataPathArr[g] = m;
                            var V = e.validate(h);
                            h.baseId = O, e.util.varOccurences(V, y) < 2 ? a += " " + e.util.varReplace(V, y, W) + " " : a += " var " + y + " = " + W + "; " + V + " ", a += " if (!" + f + ") { errors = " + d + "; if (validate.errors !== null) { if (errors) validate.errors.length = errors; else validate.errors = null; } delete " + u + "[" + m + "]; }  ", e.compositeRule = h.compositeRule = B
                        } else {
                            h.schema = k, h.schemaPath = e.schemaPath + ".additionalProperties", h.errSchemaPath = e.errSchemaPath + "/additionalProperties", h.errorPath = e.opts._errorDataPathProperty ? e.errorPath : e.util.getPathExpr(e.errorPath, m, e.opts.jsonPointers);
                            W = u + "[" + m + "]";
                            h.dataPathArr[g] = m;
                            V = e.validate(h);
                            h.baseId = O, e.util.varOccurences(V, y) < 2 ? a += " " + e.util.varReplace(V, y, W) + " " : a += " var " + y + " = " + W + "; " + V + " ", c && (a += " if (!" + f + ") break; ")
                        } e.errorPath = U
                }
                _ && (a += " } "), a += " }  ", c && (a += " if (" + f + ") { ", p += "}")
            }
            var z = e.opts.useDefaults && !e.compositeRule;
            if (w.length) {
                var X = w;
                if (X)
                    for (var Q, G = -1, K = X.length - 1; G < K;) {
                        var J = i[Q = X[G += 1]];
                        if (e.opts.strictKeywords ? "object" == typeof J && Object.keys(J).length > 0 || !1 === J : e.util.schemaHasRules(J, e.RULES.all)) {
                            var Z = e.util.getProperty(Q),
                                ee = (W = u + Z, z && void 0 !== J.default);
                            h.schema = J, h.schemaPath = s + Z, h.errSchemaPath = l + "/" + e.util.escapeFragment(Q), h.errorPath = e.util.getPath(e.errorPath, Q, e.opts.jsonPointers), h.dataPathArr[g] = e.util.toQuotedString(Q);
                            V = e.validate(h);
                            if (h.baseId = O, e.util.varOccurences(V, y) < 2) {
                                V = e.util.varReplace(V, y, W);
                                var te = W
                            } else {
                                te = y;
                                a += " var " + y + " = " + W + "; "
                            }
                            if (ee) a += " " + V + " ";
                            else {
                                if (F && F[Q]) {
                                    a += " if ( " + te + " === undefined ", D && (a += " || ! Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(Q) + "') "), a += ") { " + f + " = false; ";
                                    U = e.errorPath, q = l;
                                    var re, ae = e.util.escapeQuotes(Q);
                                    e.opts._errorDataPathProperty && (e.errorPath = e.util.getPath(U, Q, e.opts.jsonPointers)), l = e.errSchemaPath + "/required", (re = re || []).push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'required' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { missingProperty: '" + ae + "' } ", !1 !== e.opts.messages && (a += " , message: '", e.opts._errorDataPathProperty ? a += "is a required property" : a += "should have required property \\'" + ae + "\\'", a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
                                    Y = a;
                                    a = re.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + Y + "]); " : a += " validate.errors = [" + Y + "]; return false; " : a += " var err = " + Y + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", l = q, e.errorPath = U, a += " } else { "
                                } else c ? (a += " if ( " + te + " === undefined ", D && (a += " || ! Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(Q) + "') "), a += ") { " + f + " = true; } else { ") : (a += " if (" + te + " !== undefined ", D && (a += " &&   Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(Q) + "') "), a += " ) { ");
                                a += " " + V + " } "
                            }
                        }
                        c && (a += " if (" + f + ") { ", p += "}")
                    }
            }
            if (P.length) {
                var ne = P;
                if (ne)
                    for (var oe, ie = -1, se = ne.length - 1; ie < se;) {
                        J = E[oe = ne[ie += 1]];
                        if (e.opts.strictKeywords ? "object" == typeof J && Object.keys(J).length > 0 || !1 === J : e.util.schemaHasRules(J, e.RULES.all)) {
                            h.schema = J, h.schemaPath = e.schemaPath + ".patternProperties" + e.util.getProperty(oe), h.errSchemaPath = e.errSchemaPath + "/patternProperties/" + e.util.escapeFragment(oe), a += D ? " " + b + " = " + b + " || Object.keys(" + u + "); for (var " + v + "=0; " + v + "<" + b + ".length; " + v + "++) { var " + m + " = " + b + "[" + v + "]; " : " for (var " + m + " in " + u + ") { ", a += " if (" + e.usePattern(oe) + ".test(" + m + ")) { ", h.errorPath = e.util.getPathExpr(e.errorPath, m, e.opts.jsonPointers);
                            W = u + "[" + m + "]";
                            h.dataPathArr[g] = m;
                            V = e.validate(h);
                            h.baseId = O, e.util.varOccurences(V, y) < 2 ? a += " " + e.util.varReplace(V, y, W) + " " : a += " var " + y + " = " + W + "; " + V + " ", c && (a += " if (!" + f + ") break; "), a += " } ", c && (a += " else " + f + " = true; "), a += " }  ", c && (a += " if (" + f + ") { ", p += "}")
                        }
                    }
            }
            return c && (a += " " + p + " if (" + d + " == errors) {"), a
        },
        propertyNames: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "errs__" + n,
                h = e.util.copy(e);
            h.level++;
            var p = "valid" + h.level;
            if (a += "var " + d + " = errors;", e.opts.strictKeywords ? "object" == typeof i && Object.keys(i).length > 0 || !1 === i : e.util.schemaHasRules(i, e.RULES.all)) {
                h.schema = i, h.schemaPath = s, h.errSchemaPath = l;
                var f = "key" + n,
                    m = "idx" + n,
                    v = "i" + n,
                    g = "' + " + f + " + '",
                    y = "data" + (h.dataLevel = e.dataLevel + 1),
                    b = "dataProperties" + n,
                    w = e.opts.ownProperties,
                    E = e.baseId;
                w && (a += " var " + b + " = undefined; "), a += w ? " " + b + " = " + b + " || Object.keys(" + u + "); for (var " + m + "=0; " + m + "<" + b + ".length; " + m + "++) { var " + f + " = " + b + "[" + m + "]; " : " for (var " + f + " in " + u + ") { ", a += " var startErrs" + n + " = errors; ";
                var P = f,
                    k = e.compositeRule;
                e.compositeRule = h.compositeRule = !0;
                var _ = e.validate(h);
                h.baseId = E, e.util.varOccurences(_, y) < 2 ? a += " " + e.util.varReplace(_, y, P) + " " : a += " var " + y + " = " + P + "; " + _ + " ", e.compositeRule = h.compositeRule = k, a += " if (!" + p + ") { for (var " + v + "=startErrs" + n + "; " + v + "<errors; " + v + "++) { vErrors[" + v + "].propertyName = " + f + "; }   var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'propertyNames' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { propertyName: '" + g + "' } ", !1 !== e.opts.messages && (a += " , message: 'property name \\'" + g + "\\' is invalid' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", !e.compositeRule && c && (e.async ? a += " throw new ValidationError(vErrors); " : a += " validate.errors = vErrors; return false; "), c && (a += " break; "), a += " } }"
            }
            return c && (a += "  if (" + d + " == errors) {"), a
        },
        required: function(e, t, r) {
            var a = " ",
                n = e.level,
                o = e.dataLevel,
                i = e.schema[t],
                s = e.schemaPath + e.util.getProperty(t),
                l = e.errSchemaPath + "/" + t,
                c = !e.opts.allErrors,
                u = "data" + (o || ""),
                d = "valid" + n,
                h = e.opts.$data && i && i.$data;
            h && (a += " var schema" + n + " = " + e.util.getData(i.$data, o, e.dataPathArr) + "; ");
            var p = "schema" + n;
            if (!h)
                if (i.length < e.opts.loopRequired && e.schema.properties && Object.keys(e.schema.properties).length) {
                    var f = [],
                        m = i;
                    if (m)
                        for (var v, g = -1, y = m.length - 1; g < y;) {
                            v = m[g += 1];
                            var b = e.schema.properties[v];
                            b && (e.opts.strictKeywords ? "object" == typeof b && Object.keys(b).length > 0 || !1 === b : e.util.schemaHasRules(b, e.RULES.all)) || (f[f.length] = v)
                        }
                } else f = i;
            if (h || f.length) {
                var w = e.errorPath,
                    E = h || f.length >= e.opts.loopRequired,
                    P = e.opts.ownProperties;
                if (c)
                    if (a += " var missing" + n + "; ", E) {
                        h || (a += " var " + p + " = validate.schema" + s + "; ");
                        var k = "' + " + (D = "schema" + n + "[" + (C = "i" + n) + "]") + " + '";
                        e.opts._errorDataPathProperty && (e.errorPath = e.util.getPathExpr(w, D, e.opts.jsonPointers)), a += " var " + d + " = true; ", h && (a += " if (schema" + n + " === undefined) " + d + " = true; else if (!Array.isArray(schema" + n + ")) " + d + " = false; else {"), a += " for (var " + C + " = 0; " + C + " < " + p + ".length; " + C + "++) { " + d + " = " + u + "[" + p + "[" + C + "]] !== undefined ", P && (a += " &&   Object.prototype.hasOwnProperty.call(" + u + ", " + p + "[" + C + "]) "), a += "; if (!" + d + ") break; } ", h && (a += "  }  "), a += "  if (!" + d + ") {   ", (x = x || []).push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'required' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { missingProperty: '" + k + "' } ", !1 !== e.opts.messages && (a += " , message: '", e.opts._errorDataPathProperty ? a += "is a required property" : a += "should have required property \\'" + k + "\\'", a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
                        var _ = a;
                        a = x.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + _ + "]); " : a += " validate.errors = [" + _ + "]; return false; " : a += " var err = " + _ + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " } else { "
                    } else {
                        a += " if ( ";
                        var S = f;
                        if (S)
                            for (var C = -1, T = S.length - 1; C < T;) {
                                R = S[C += 1], C && (a += " || "), a += " ( ( " + (M = u + (A = e.util.getProperty(R))) + " === undefined ", P && (a += " || ! Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(R) + "') "), a += ") && (missing" + n + " = " + e.util.toQuotedString(e.opts.jsonPointers ? R : A) + ") ) "
                            }
                        a += ") {  ";
                        var x;
                        k = "' + " + (D = "missing" + n) + " + '";
                        e.opts._errorDataPathProperty && (e.errorPath = e.opts.jsonPointers ? e.util.getPathExpr(w, D, !0) : w + " + " + D), (x = x || []).push(a), a = "", !1 !== e.createErrors ? (a += " { keyword: 'required' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { missingProperty: '" + k + "' } ", !1 !== e.opts.messages && (a += " , message: '", e.opts._errorDataPathProperty ? a += "is a required property" : a += "should have required property \\'" + k + "\\'", a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ";
                        _ = a;
                        a = x.pop(), !e.compositeRule && c ? e.async ? a += " throw new ValidationError([" + _ + "]); " : a += " validate.errors = [" + _ + "]; return false; " : a += " var err = " + _ + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", a += " } else { "
                    }
                else if (E) {
                    h || (a += " var " + p + " = validate.schema" + s + "; ");
                    var D;
                    k = "' + " + (D = "schema" + n + "[" + (C = "i" + n) + "]") + " + '";
                    e.opts._errorDataPathProperty && (e.errorPath = e.util.getPathExpr(w, D, e.opts.jsonPointers)), h && (a += " if (" + p + " && !Array.isArray(" + p + ")) {  var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'required' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { missingProperty: '" + k + "' } ", !1 !== e.opts.messages && (a += " , message: '", e.opts._errorDataPathProperty ? a += "is a required property" : a += "should have required property \\'" + k + "\\'", a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; } else if (" + p + " !== undefined) { "), a += " for (var " + C + " = 0; " + C + " < " + p + ".length; " + C + "++) { if (" + u + "[" + p + "[" + C + "]] === undefined ", P && (a += " || ! Object.prototype.hasOwnProperty.call(" + u + ", " + p + "[" + C + "]) "), a += ") {  var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'required' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { missingProperty: '" + k + "' } ", !1 !== e.opts.messages && (a += " , message: '", e.opts._errorDataPathProperty ? a += "is a required property" : a += "should have required property \\'" + k + "\\'", a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; } } ", h && (a += "  }  ")
                } else {
                    var O = f;
                    if (O)
                        for (var R, F = -1, $ = O.length - 1; F < $;) {
                            R = O[F += 1];
                            var A = e.util.getProperty(R),
                                M = (k = e.util.escapeQuotes(R), u + A);
                            e.opts._errorDataPathProperty && (e.errorPath = e.util.getPath(w, R, e.opts.jsonPointers)), a += " if ( " + M + " === undefined ", P && (a += " || ! Object.prototype.hasOwnProperty.call(" + u + ", '" + e.util.escapeQuotes(R) + "') "), a += ") {  var err =   ", !1 !== e.createErrors ? (a += " { keyword: 'required' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(l) + " , params: { missingProperty: '" + k + "' } ", !1 !== e.opts.messages && (a += " , message: '", e.opts._errorDataPathProperty ? a += "is a required property" : a += "should have required property \\'" + k + "\\'", a += "' "), e.opts.verbose && (a += " , schema: validate.schema" + s + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + u + " "), a += " } ") : a += " {} ", a += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; } "
                        }
                }
                e.errorPath = w
            } else c && (a += " if (true) {");
            return a
        },
        uniqueItems: function(e, t, r) {
            var a, n = " ",
                o = e.level,
                i = e.dataLevel,
                s = e.schema[t],
                l = e.schemaPath + e.util.getProperty(t),
                c = e.errSchemaPath + "/" + t,
                u = !e.opts.allErrors,
                d = "data" + (i || ""),
                h = "valid" + o,
                p = e.opts.$data && s && s.$data;
            if (p ? (n += " var schema" + o + " = " + e.util.getData(s.$data, i, e.dataPathArr) + "; ", a = "schema" + o) : a = s, (s || p) && !1 !== e.opts.uniqueItems) {
                p && (n += " var " + h + "; if (" + a + " === false || " + a + " === undefined) " + h + " = true; else if (typeof " + a + " != 'boolean') " + h + " = false; else { "), n += " var i = " + d + ".length , " + h + " = true , j; if (i > 1) { ";
                var f = e.schema.items && e.schema.items.type,
                    m = Array.isArray(f);
                if (!f || "object" == f || "array" == f || m && (f.indexOf("object") >= 0 || f.indexOf("array") >= 0)) n += " outer: for (;i--;) { for (j = i; j--;) { if (equal(" + d + "[i], " + d + "[j])) { " + h + " = false; break outer; } } } ";
                else {
                    n += " var itemIndices = {}, item; for (;i--;) { var item = " + d + "[i]; ";
                    var v = "checkDataType" + (m ? "s" : "");
                    n += " if (" + e.util[v](f, "item", e.opts.strictNumbers, !0) + ") continue; ", m && (n += " if (typeof item == 'string') item = '\"' + item; "), n += " if (typeof itemIndices[item] == 'number') { " + h + " = false; j = itemIndices[item]; break; } itemIndices[item] = i; } "
                }
                n += " } ", p && (n += "  }  "), n += " if (!" + h + ") {   ";
                var g = g || [];
                g.push(n), n = "", !1 !== e.createErrors ? (n += " { keyword: 'uniqueItems' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(c) + " , params: { i: i, j: j } ", !1 !== e.opts.messages && (n += " , message: 'should NOT have duplicate items (items ## ' + j + ' and ' + i + ' are identical)' "), e.opts.verbose && (n += " , schema:  ", n += p ? "validate.schema" + l : "" + s, n += "         , parentSchema: validate.schema" + e.schemaPath + " , data: " + d + " "), n += " } ") : n += " {} ";
                var y = n;
                n = g.pop(), !e.compositeRule && u ? e.async ? n += " throw new ValidationError([" + y + "]); " : n += " validate.errors = [" + y + "]; return false; " : n += " var err = " + y + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", n += " } ", u && (n += " else { ")
            } else u && (n += " if (true) { ");
            return n
        },
        validate: Xs
    },
    Rl = ps.toHash,
    Fl = ["multipleOf", "maximum", "exclusiveMaximum", "minimum", "exclusiveMinimum", "maxLength", "minLength", "pattern", "additionalItems", "maxItems", "minItems", "uniqueItems", "maxProperties", "minProperties", "required", "additionalProperties", "enum", "format", "const"],
    $l = function(e, t) {
        for (var r = 0; r < t.length; r++) {
            e = JSON.parse(JSON.stringify(e));
            var a, n = t[r].split("/"),
                o = e;
            for (a = 1; a < n.length; a++) o = o[n[a]];
            for (a = 0; a < Fl.length; a++) {
                var i = Fl[a],
                    s = o[i];
                s && (o[i] = {
                    anyOf: [s, {
                        $ref: "https://raw.githubusercontent.com/ajv-validator/ajv/master/lib/refs/data.json#"
                    }]
                })
            }
        }
        return e
    },
    Al = Bs.MissingRef,
    Ml = function e(t, r, a) {
        var n = this;
        if ("function" != typeof this._opts.loadSchema) throw new Error("options.loadSchema should be a function");
        "function" == typeof r && (a = r, r = void 0);
        var o = i(t).then((function() {
            var e = n._addSchema(t, void 0, r);
            return e.validate || s(e)
        }));
        a && o.then((function(e) {
            a(null, e)
        }), a);
        return o;

        function i(t) {
            var r = t.$schema;
            return r && !n.getSchema(r) ? e.call(n, {
                $ref: r
            }, !0) : Promise.resolve()
        }

        function s(e) {
            try {
                return n._compile(e)
            } catch (t) {
                if (t instanceof Al) return function(t) {
                    var a = t.missingSchema;
                    if (c(a)) throw new Error("Schema " + a + " is loaded but " + t.missingRef + " cannot be resolved");
                    var o = n._loadingSchemas[a];
                    o || (o = n._loadingSchemas[a] = n._opts.loadSchema(a)).then(l, l);
                    return o.then((function(e) {
                        if (!c(a)) return i(e).then((function() {
                            c(a) || n.addSchema(e, a, void 0, r)
                        }))
                    })).then((function() {
                        return s(e)
                    }));

                    function l() {
                        delete n._loadingSchemas[a]
                    }

                    function c(e) {
                        return n._refs[e] || n._schemas[e]
                    }
                }(t);
                throw t
            }
        }
    };
var Ll = function(e, t, r) {
    var a, n, o = " ",
        i = e.level,
        s = e.dataLevel,
        l = e.schema[t],
        c = e.schemaPath + e.util.getProperty(t),
        u = e.errSchemaPath + "/" + t,
        d = !e.opts.allErrors,
        h = "data" + (s || ""),
        p = "valid" + i,
        f = "errs__" + i,
        m = e.opts.$data && l && l.$data;
    m ? (o += " var schema" + i + " = " + e.util.getData(l.$data, s, e.dataPathArr) + "; ", n = "schema" + i) : n = l;
    var v, g, y, b, w, E = this,
        P = "definition" + i,
        k = E.definition,
        _ = "";
    if (m && k.$data) {
        w = "keywordValidate" + i;
        var S = k.validateSchema;
        o += " var " + P + " = RULES.custom['" + t + "'].definition; var " + w + " = " + P + ".validate;"
    } else {
        if (!(b = e.useCustomRule(E, l, e.schema, e))) return;
        n = "validate.schema" + c, w = b.code, v = k.compile, g = k.inline, y = k.macro
    }
    var C = w + ".errors",
        T = "i" + i,
        x = "ruleErr" + i,
        D = k.async;
    if (D && !e.async) throw new Error("async keyword in sync schema");
    if (g || y || (o += C + " = null;"), o += "var " + f + " = errors;var " + p + ";", m && k.$data && (_ += "}", o += " if (" + n + " === undefined) { " + p + " = true; } else { ", S && (_ += "}", o += " " + p + " = " + P + ".validateSchema(" + n + "); if (" + p + ") { ")), g) k.statements ? o += " " + b.validate + " " : o += " " + p + " = " + b.validate + "; ";
    else if (y) {
        var O = e.util.copy(e);
        _ = "";
        O.level++;
        var R = "valid" + O.level;
        O.schema = b.validate, O.schemaPath = "";
        var F = e.compositeRule;
        e.compositeRule = O.compositeRule = !0;
        var $ = e.validate(O).replace(/validate\.schema/g, w);
        e.compositeRule = O.compositeRule = F, o += " " + $
    } else {
        (N = N || []).push(o), o = "", o += "  " + w + ".call( ", e.opts.passContext ? o += "this" : o += "self", v || !1 === k.schema ? o += " , " + h + " " : o += " , " + n + " , " + h + " , validate.schema" + e.schemaPath + " ", o += " , (dataPath || '')", '""' != e.errorPath && (o += " + " + e.errorPath);
        var A = s ? "data" + (s - 1 || "") : "parentData",
            M = s ? e.dataPathArr[s] : "parentDataProperty",
            L = o += " , " + A + " , " + M + " , rootData )  ";
        o = N.pop(), !1 === k.errors ? (o += " " + p + " = ", D && (o += "await "), o += L + "; ") : o += D ? " var " + (C = "customErrors" + i) + " = null; try { " + p + " = await " + L + "; } catch (e) { " + p + " = false; if (e instanceof ValidationError) " + C + " = e.errors; else throw e; } " : " " + C + " = null; " + p + " = " + L + "; "
    }
    if (k.modifying && (o += " if (" + A + ") " + h + " = " + A + "[" + M + "];"), o += "" + _, k.valid) d && (o += " if (true) { ");
    else {
        var N;
        o += " if ( ", void 0 === k.valid ? (o += " !", o += y ? "" + R : "" + p) : o += " " + !k.valid + " ", o += ") { ", a = E.keyword, (N = N || []).push(o), o = "", (N = N || []).push(o), o = "", !1 !== e.createErrors ? (o += " { keyword: '" + (a || "custom") + "' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(u) + " , params: { keyword: '" + E.keyword + "' } ", !1 !== e.opts.messages && (o += " , message: 'should pass \"" + E.keyword + "\" keyword validation' "), e.opts.verbose && (o += " , schema: validate.schema" + c + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + h + " "), o += " } ") : o += " {} ";
        var I = o;
        o = N.pop(), !e.compositeRule && d ? e.async ? o += " throw new ValidationError([" + I + "]); " : o += " validate.errors = [" + I + "]; return false; " : o += " var err = " + I + ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ";
        var j = o;
        o = N.pop(), g ? k.errors ? "full" != k.errors && (o += "  for (var " + T + "=" + f + "; " + T + "<errors; " + T + "++) { var " + x + " = vErrors[" + T + "]; if (" + x + ".dataPath === undefined) " + x + ".dataPath = (dataPath || '') + " + e.errorPath + "; if (" + x + ".schemaPath === undefined) { " + x + '.schemaPath = "' + u + '"; } ', e.opts.verbose && (o += " " + x + ".schema = " + n + "; " + x + ".data = " + h + "; "), o += " } ") : !1 === k.errors ? o += " " + j + " " : (o += " if (" + f + " == errors) { " + j + " } else {  for (var " + T + "=" + f + "; " + T + "<errors; " + T + "++) { var " + x + " = vErrors[" + T + "]; if (" + x + ".dataPath === undefined) " + x + ".dataPath = (dataPath || '') + " + e.errorPath + "; if (" + x + ".schemaPath === undefined) { " + x + '.schemaPath = "' + u + '"; } ', e.opts.verbose && (o += " " + x + ".schema = " + n + "; " + x + ".data = " + h + "; "), o += " } } ") : y ? (o += "   var err =   ", !1 !== e.createErrors ? (o += " { keyword: '" + (a || "custom") + "' , dataPath: (dataPath || '') + " + e.errorPath + " , schemaPath: " + e.util.toQuotedString(u) + " , params: { keyword: '" + E.keyword + "' } ", !1 !== e.opts.messages && (o += " , message: 'should pass \"" + E.keyword + "\" keyword validation' "), e.opts.verbose && (o += " , schema: validate.schema" + c + " , parentSchema: validate.schema" + e.schemaPath + " , data: " + h + " "), o += " } ") : o += " {} ", o += ";  if (vErrors === null) vErrors = [err]; else vErrors.push(err); errors++; ", !e.compositeRule && d && (e.async ? o += " throw new ValidationError(vErrors); " : o += " validate.errors = vErrors; return false; ")) : !1 === k.errors ? o += " " + j + " " : (o += " if (Array.isArray(" + C + ")) { if (vErrors === null) vErrors = " + C + "; else vErrors = vErrors.concat(" + C + "); errors = vErrors.length;  for (var " + T + "=" + f + "; " + T + "<errors; " + T + "++) { var " + x + " = vErrors[" + T + "]; if (" + x + ".dataPath === undefined) " + x + ".dataPath = (dataPath || '') + " + e.errorPath + ";  " + x + '.schemaPath = "' + u + '";  ', e.opts.verbose && (o += " " + x + ".schema = " + n + "; " + x + ".data = " + h + "; "), o += " } } else { " + j + " } "), o += " } ", d && (o += " else { ")
    }
    return o
};
var Nl = {
        $schema: "http://json-schema.org/draft-07/schema#",
        $id: "http://json-schema.org/draft-07/schema#",
        title: "Core schema meta-schema",
        definitions: {
            schemaArray: {
                type: "array",
                minItems: 1,
                items: {
                    $ref: "#"
                }
            },
            nonNegativeInteger: {
                type: "integer",
                minimum: 0
            },
            nonNegativeIntegerDefault0: {
                allOf: [{
                    $ref: "#/definitions/nonNegativeInteger"
                }, {
                    default: 0
                }]
            },
            simpleTypes: {
                enum: ["array", "boolean", "integer", "null", "number", "object", "string"]
            },
            stringArray: {
                type: "array",
                items: {
                    type: "string"
                },
                uniqueItems: !0,
                default: []
            }
        },
        type: ["object", "boolean"],
        properties: {
            $id: {
                type: "string",
                format: "uri-reference"
            },
            $schema: {
                type: "string",
                format: "uri"
            },
            $ref: {
                type: "string",
                format: "uri-reference"
            },
            $comment: {
                type: "string"
            },
            title: {
                type: "string"
            },
            description: {
                type: "string"
            },
            default: !0,
            readOnly: {
                type: "boolean",
                default: !1
            },
            examples: {
                type: "array",
                items: !0
            },
            multipleOf: {
                type: "number",
                exclusiveMinimum: 0
            },
            maximum: {
                type: "number"
            },
            exclusiveMaximum: {
                type: "number"
            },
            minimum: {
                type: "number"
            },
            exclusiveMinimum: {
                type: "number"
            },
            maxLength: {
                $ref: "#/definitions/nonNegativeInteger"
            },
            minLength: {
                $ref: "#/definitions/nonNegativeIntegerDefault0"
            },
            pattern: {
                type: "string",
                format: "regex"
            },
            additionalItems: {
                $ref: "#"
            },
            items: {
                anyOf: [{
                    $ref: "#"
                }, {
                    $ref: "#/definitions/schemaArray"
                }],
                default: !0
            },
            maxItems: {
                $ref: "#/definitions/nonNegativeInteger"
            },
            minItems: {
                $ref: "#/definitions/nonNegativeIntegerDefault0"
            },
            uniqueItems: {
                type: "boolean",
                default: !1
            },
            contains: {
                $ref: "#"
            },
            maxProperties: {
                $ref: "#/definitions/nonNegativeInteger"
            },
            minProperties: {
                $ref: "#/definitions/nonNegativeIntegerDefault0"
            },
            required: {
                $ref: "#/definitions/stringArray"
            },
            additionalProperties: {
                $ref: "#"
            },
            definitions: {
                type: "object",
                additionalProperties: {
                    $ref: "#"
                },
                default: {}
            },
            properties: {
                type: "object",
                additionalProperties: {
                    $ref: "#"
                },
                default: {}
            },
            patternProperties: {
                type: "object",
                additionalProperties: {
                    $ref: "#"
                },
                propertyNames: {
                    format: "regex"
                },
                default: {}
            },
            dependencies: {
                type: "object",
                additionalProperties: {
                    anyOf: [{
                        $ref: "#"
                    }, {
                        $ref: "#/definitions/stringArray"
                    }]
                }
            },
            propertyNames: {
                $ref: "#"
            },
            const: !0,
            enum: {
                type: "array",
                items: !0,
                minItems: 1,
                uniqueItems: !0
            },
            type: {
                anyOf: [{
                    $ref: "#/definitions/simpleTypes"
                }, {
                    type: "array",
                    items: {
                        $ref: "#/definitions/simpleTypes"
                    },
                    minItems: 1,
                    uniqueItems: !0
                }]
            },
            format: {
                type: "string"
            },
            contentMediaType: {
                type: "string"
            },
            contentEncoding: {
                type: "string"
            },
            if: {
                $ref: "#"
            },
            then: {
                $ref: "#"
            },
            else: {
                $ref: "#"
            },
            allOf: {
                $ref: "#/definitions/schemaArray"
            },
            anyOf: {
                $ref: "#/definitions/schemaArray"
            },
            oneOf: {
                $ref: "#/definitions/schemaArray"
            },
            not: {
                $ref: "#"
            }
        },
        default: !0
    },
    Il = {
        $id: "https://github.com/ajv-validator/ajv/blob/master/lib/definition_schema.js",
        definitions: {
            simpleTypes: Nl.definitions.simpleTypes
        },
        type: "object",
        dependencies: {
            schema: ["validate"],
            $data: ["validate"],
            statements: ["inline"],
            valid: {
                not: {
                    required: ["macro"]
                }
            }
        },
        properties: {
            type: Nl.properties.type,
            schema: {
                type: "boolean"
            },
            statements: {
                type: "boolean"
            },
            dependencies: {
                type: "array",
                items: {
                    type: "string"
                }
            },
            metaSchema: {
                type: "object"
            },
            modifying: {
                type: "boolean"
            },
            valid: {
                type: "boolean"
            },
            $data: {
                type: "boolean"
            },
            async: {
                type: "boolean"
            },
            errors: {
                anyOf: [{
                    type: "boolean"
                }, {
                    const: "full"
                }]
            }
        }
    },
    jl = /^[a-z_$][a-z0-9_$-]*$/i,
    Ul = function(e, t) {
        var r = this.RULES;
        if (r.keywords[e]) throw new Error("Keyword " + e + " is already defined");
        if (!jl.test(e)) throw new Error("Keyword " + e + " is not a valid identifier");
        if (t) {
            this.validateKeyword(t, !0);
            var a = t.type;
            if (Array.isArray(a))
                for (var n = 0; n < a.length; n++) i(e, a[n], t);
            else i(e, a, t);
            var o = t.metaSchema;
            o && (t.$data && this._opts.$data && (o = {
                anyOf: [o, {
                    $ref: "https://raw.githubusercontent.com/ajv-validator/ajv/master/lib/refs/data.json#"
                }]
            }), t.validateSchema = this.compile(o, !0))
        }

        function i(e, t, a) {
            for (var n, o = 0; o < r.length; o++) {
                var i = r[o];
                if (i.type == t) {
                    n = i;
                    break
                }
            }
            n || (n = {
                type: t,
                rules: []
            }, r.push(n));
            var s = {
                keyword: e,
                definition: a,
                custom: !0,
                code: Ll,
                implements: a.implements
            };
            n.rules.push(s), r.custom[e] = s
        }
        return r.keywords[e] = r.all[e] = !0, this
    },
    Hl = function(e) {
        var t = this.RULES.custom[e];
        return t ? t.definition : this.RULES.keywords[e] || !1
    },
    ql = function(e) {
        var t = this.RULES;
        delete t.keywords[e], delete t.all[e], delete t.custom[e];
        for (var r = 0; r < t.length; r++)
            for (var a = t[r].rules, n = 0; n < a.length; n++)
                if (a[n].keyword == e) {
                    a.splice(n, 1);
                    break
                } return this
    },
    Yl = function e(t, r) {
        e.errors = null;
        var a = this._validateKeyword = this._validateKeyword || this.compile(Il, !0);
        if (a(t)) return !0;
        if (e.errors = a.errors, r) throw new Error("custom keyword definition is invalid: " + this.errorsText(a.errors));
        return !1
    };
var Bl = {
        $schema: "http://json-schema.org/draft-07/schema#",
        $id: "https://raw.githubusercontent.com/ajv-validator/ajv/master/lib/refs/data.json#",
        description: "Meta-schema for $data reference (JSON Schema extension proposal)",
        type: "object",
        required: ["$data"],
        properties: {
            $data: {
                type: "string",
                anyOf: [{
                    format: "relative-json-pointer"
                }, {
                    format: "json-pointer"
                }]
            }
        },
        additionalProperties: !1
    },
    Wl = Ql;
Ql.prototype.validate = function(e, t) {
    var r;
    if ("string" == typeof e) {
        if (!(r = this.getSchema(e))) throw new Error('no schema with key or ref "' + e + '"')
    } else {
        var a = this._addSchema(e);
        r = a.validate || this._compile(a)
    }
    var n = r(t);
    !0 !== r.$async && (this.errors = r.errors);
    return n
}, Ql.prototype.compile = function(e, t) {
    var r = this._addSchema(e, void 0, t);
    return r.validate || this._compile(r)
}, Ql.prototype.addSchema = function(e, t, r, a) {
    if (Array.isArray(e)) {
        for (var n = 0; n < e.length; n++) this.addSchema(e[n], void 0, r, a);
        return this
    }
    var o = this._getId(e);
    if (void 0 !== o && "string" != typeof o) throw new Error("schema id must be string");
    return tc(this, t = Ds.normalizeId(t || o)), this._schemas[t] = this._addSchema(e, r, a, !0), this
}, Ql.prototype.addMetaSchema = function(e, t, r) {
    return this.addSchema(e, t, r, !0), this
}, Ql.prototype.validateSchema = function(e, t) {
    var r = e.$schema;
    if (void 0 !== r && "string" != typeof r) throw new Error("$schema must be a string");
    if (!(r = r || this._opts.defaultMeta || function(e) {
            var t = e._opts.meta;
            return e._opts.defaultMeta = "object" == typeof t ? e._getId(t) || t : e.getSchema(Vl) ? Vl : void 0, e._opts.defaultMeta
        }(this))) return this.logger.warn("meta-schema not available"), this.errors = null, !0;
    var a = this.validate(r, e);
    if (!a && t) {
        var n = "schema is invalid: " + this.errorsText();
        if ("log" != this._opts.validateSchema) throw new Error(n);
        this.logger.error(n)
    }
    return a
}, Ql.prototype.getSchema = function(e) {
    var t = Gl(this, e);
    switch (typeof t) {
        case "object":
            return t.validate || this._compile(t);
        case "string":
            return this.getSchema(t);
        case "undefined":
            return function(e, t) {
                var r = Ds.schema.call(e, {
                    schema: {}
                }, t);
                if (r) {
                    var a = r.schema,
                        n = r.root,
                        o = r.baseId,
                        i = Ks.call(e, a, n, void 0, o);
                    return e._fragments[t] = new Ts({
                        ref: t,
                        fragment: !0,
                        schema: a,
                        root: n,
                        baseId: o,
                        validate: i
                    }), i
                }
            }(this, e)
    }
}, Ql.prototype.removeSchema = function(e) {
    if (e instanceof RegExp) return Kl(this, this._schemas, e), Kl(this, this._refs, e), this;
    switch (typeof e) {
        case "undefined":
            return Kl(this, this._schemas), Kl(this, this._refs), this._cache.clear(), this;
        case "string":
            var t = Gl(this, e);
            return t && this._cache.del(t.cacheKey), delete this._schemas[e], delete this._refs[e], this;
        case "object":
            var r = this._opts.serialize,
                a = r ? r(e) : e;
            this._cache.del(a);
            var n = this._getId(e);
            n && (n = Ds.normalizeId(n), delete this._schemas[n], delete this._refs[n])
    }
    return this
}, Ql.prototype.addFormat = function(e, t) {
    "string" == typeof t && (t = new RegExp(t));
    return this._formats[e] = t, this
}, Ql.prototype.errorsText = function(e, t) {
    if (!(e = e || this.errors)) return "No errors";
    for (var r = void 0 === (t = t || {}).separator ? ", " : t.separator, a = void 0 === t.dataVar ? "data" : t.dataVar, n = "", o = 0; o < e.length; o++) {
        var i = e[o];
        i && (n += a + i.dataPath + " " + i.message + r)
    }
    return n.slice(0, -r.length)
}, Ql.prototype._addSchema = function(e, t, r, a) {
    if ("object" != typeof e && "boolean" != typeof e) throw new Error("schema should be object or boolean");
    var n = this._opts.serialize,
        o = n ? n(e) : e,
        i = this._cache.get(o);
    if (i) return i;
    a = a || !1 !== this._opts.addUsedSchema;
    var s = Ds.normalizeId(this._getId(e));
    s && a && tc(this, s);
    var l, c = !1 !== this._opts.validateSchema && !t;
    c && !(l = s && s == Ds.normalizeId(e.$schema)) && this.validateSchema(e, !0);
    var u = Ds.ids.call(this, e),
        d = new Ts({
            id: s,
            schema: e,
            localRefs: u,
            cacheKey: o,
            meta: r
        });
    "#" != s[0] && a && (this._refs[s] = d);
    this._cache.put(o, d), c && l && this.validateSchema(e, !0);
    return d
}, Ql.prototype._compile = function(e, t) {
    if (e.compiling) return e.validate = n, n.schema = e.schema, n.errors = null, n.root = t || n, !0 === e.schema.$async && (n.$async = !0), n;
    var r, a;
    e.compiling = !0, e.meta && (r = this._opts, this._opts = this._metaOpts);
    try {
        a = Ks.call(this, e.schema, t, e.localRefs)
    } catch (t) {
        throw delete e.validate, t
    } finally {
        e.compiling = !1, e.meta && (this._opts = r)
    }
    return e.validate = a, e.refs = a.refs, e.refVal = a.refVal, e.root = a.root, a;

    function n() {
        var t = e.validate,
            r = t.apply(this, arguments);
        return n.errors = t.errors, r
    }
}, Ql.prototype.compileAsync = Ml, Ql.prototype.addKeyword = Ul, Ql.prototype.getKeyword = Hl, Ql.prototype.removeKeyword = ql, Ql.prototype.validateKeyword = Yl, Ql.ValidationError = Bs.Validation, Ql.MissingRefError = Bs.MissingRef, Ql.$dataMetaSchema = $l;
var Vl = "http://json-schema.org/draft-07/schema",
    zl = ["removeAdditional", "useDefaults", "coerceTypes", "strictDefaults"],
    Xl = ["/properties"];

function Ql(e) {
    if (!(this instanceof Ql)) return new Ql(e);
    var t, r;
    e = this._opts = ps.copy(e) || {},
        function(e) {
            var t = e._opts.logger;
            if (!1 === t) e.logger = {
                log: rc,
                warn: rc,
                error: rc
            };
            else {
                if (void 0 === t && (t = console), !("object" == typeof t && t.log && t.warn && t.error)) throw new Error("logger must implement log, warn and error methods");
                e.logger = t
            }
        }(this), this._schemas = {}, this._refs = {}, this._fragments = {}, this._formats = yl(e.format), this._cache = e.cache || new il, this._loadingSchemas = {}, this._compilations = [], this.RULES = ((t = [{
            type: "number",
            rules: [{
                maximum: ["exclusiveMaximum"]
            }, {
                minimum: ["exclusiveMinimum"]
            }, "multipleOf", "format"]
        }, {
            type: "string",
            rules: ["maxLength", "minLength", "pattern", "format"]
        }, {
            type: "array",
            rules: ["maxItems", "minItems", "items", "contains", "uniqueItems"]
        }, {
            type: "object",
            rules: ["maxProperties", "minProperties", "required", "dependencies", "propertyNames", {
                properties: ["additionalProperties", "patternProperties"]
            }]
        }, {
            rules: ["$ref", "const", "enum", "not", "anyOf", "oneOf", "allOf", "if"]
        }]).all = Rl(r = ["type", "$comment"]), t.types = Rl(["number", "integer", "string", "array", "object", "boolean", "null"]), t.forEach((function(e) {
            e.rules = e.rules.map((function(e) {
                var a;
                if ("object" == typeof e) {
                    var n = Object.keys(e)[0];
                    a = e[n], e = n, a.forEach((function(e) {
                        r.push(e), t.all[e] = !0
                    }))
                }
                return r.push(e), t.all[e] = {
                    keyword: e,
                    code: Ol[e],
                    implements: a
                }
            })), t.all.$comment = {
                keyword: "$comment",
                code: Ol.$comment
            }, e.type && (t.types[e.type] = e)
        })), t.keywords = Rl(r.concat(["$schema", "$id", "id", "$data", "$async", "title", "description", "default", "definitions", "examples", "readOnly", "writeOnly", "contentMediaType", "contentEncoding", "additionalItems", "then", "else"])), t.custom = {}, t), this._getId = function(e) {
            switch (e.schemaId) {
                case "auto":
                    return ec;
                case "id":
                    return Jl;
                default:
                    return Zl
            }
        }(e), e.loopRequired = e.loopRequired || 1 / 0, "property" == e.errorDataPath && (e._errorDataPathProperty = !0), void 0 === e.serialize && (e.serialize = zs), this._metaOpts = function(e) {
            for (var t = ps.copy(e._opts), r = 0; r < zl.length; r++) delete t[zl[r]];
            return t
        }(this), e.formats && function(e) {
            for (var t in e._opts.formats) {
                var r = e._opts.formats[t];
                e.addFormat(t, r)
            }
        }(this), e.keywords && function(e) {
            for (var t in e._opts.keywords) {
                var r = e._opts.keywords[t];
                e.addKeyword(t, r)
            }
        }(this),
        function(e) {
            var t;
            e._opts.$data && (t = Bl, e.addMetaSchema(t, t.$id, !0));
            if (!1 === e._opts.meta) return;
            var r = Nl;
            e._opts.$data && (r = $l(r, Xl));
            e.addMetaSchema(r, Vl, !0), e._refs["http://json-schema.org/schema"] = Vl
        }(this), "object" == typeof e.meta && this.addMetaSchema(e.meta), e.nullable && this.addKeyword("nullable", {
            metaSchema: {
                type: "boolean"
            }
        }),
        function(e) {
            var t = e._opts.schemas;
            if (!t) return;
            if (Array.isArray(t)) e.addSchema(t);
            else
                for (var r in t) e.addSchema(t[r], r)
        }(this)
}

function Gl(e, t) {
    return t = Ds.normalizeId(t), e._schemas[t] || e._refs[t] || e._fragments[t]
}

function Kl(e, t, r) {
    for (var a in t) {
        var n = t[a];
        n.meta || r && !r.test(a) || (e._cache.del(n.cacheKey), delete t[a])
    }
}

function Jl(e) {
    return e.$id && this.logger.warn("schema $id ignored", e.$id), e.id
}

function Zl(e) {
    return e.id && this.logger.warn("schema id ignored", e.id), e.$id
}

function ec(e) {
    if (e.$id && e.id && e.$id != e.id) throw new Error("schema $id is different from id");
    return e.$id || e.id
}

function tc(e, t) {
    if (e._schemas[t] || e._refs[t]) throw new Error('schema with key or id "' + t + '" already exists')
}

function rc() {}
const ac = new Wl({
    removeAdditional: "all",
    validateSchema: !1,
    additionalProperties: !1,
    messages: !1,
    $data: !0,
    allErrors: !0
});
class nc {
    constructor(e, t, r = {}, a = null) {
        this.service = e, this.action = t, this.data = r, this.errors = {}, this.valid = !1, this.force_validate = !1
    }
    set(e, t) {
        this.data[e] = t
    }
    setData(e) {
        this.data = {
            ...this.data,
            ...e
        }
    }
    validate() {
        var e;
        return this.errors = function(e, t, r) {
            const a = ls([e, t]);
            return !ac.validate(a, r) && ac.errors.reduce(((e, t) => {
                const {
                    keyword: r,
                    params: a,
                    dataPath: n
                } = t, o = t.params && t.params.missingProperty || n.substr(1);
                return e[o] || (e[o] = []), e[o].push({
                    keyword: r,
                    params: a
                }), e
            }), {})
        }(this.service, this.action, (e = this.data, JSON.parse(JSON.stringify(e)))), this.valid = !1 === this.errors, !1 === this.errors
    }
    getErrors(e = null) {
        return e ? this.errors[e] : this.errors
    }
    force() {
        this.force_validate = !0
    }
    unforce() {
        this.force_validate = !1
    }
    call() {
        return this.validate(), this.force(), !this.errors && uc(this.service, this.action, this.data)
    }
}
class oc extends Error {
    constructor(e) {
        console.error("API_ERROR", e), super(`API_ERROR: ${JSON.stringify(e)}`), this.loadObject(e)
    }
    loadObject(e) {
        Object.getOwnPropertyNames(e).forEach((t => {
            this[t] = e[t]
        }))
    }
    toString() {
        return JSON.stringify(this)
    }
    toJSON() {
        return JSON.stringify(this)
    }
}
const ic = "https://steam-rep.com/api.php?call=",
    sc = Ze(!1);
async function lc(e, t = null, r = null) {
    t && (r.body = JSON.stringify(t));
    const a = await async function(e, t) {
        const {
            timeout: r = 5e3
        } = t, a = new AbortController, n = setTimeout((() => a.abort()), r), o = await fetch(e, {
            ...t,
            signal: a.signal
        });
        return clearTimeout(n), o
    }(e, {
        ...r,
        headers: {
            "Content-Type": "application/json"
        }
    }), n = await a.json();
    if (200 !== a.status) throw new oc(n);
    return n
}
const cc = {};

function uc(e, t, r = {}) {
    const a = ls([e, t]);
    if (!cc[a]) throw new Error(`Wrong action ${a}`);
    return (async (e, t = null, r = {}) => (r.method = "POST", r.credentials = "include", lc(e, t, r)))(ic, {
        id: cc[a].id,
        query: r
    })
}
async function dc() {
    const e = await ((e, t = {}) => (t.method = "GET", lc(e, null, t)))(`https://steam-rep.com/api2.php?/config`);
    Object.entries(e).forEach((([e, {
        service: t,
        action: r,
        validator: a
    }]) => {
        const n = ls([t, r]);
        cc[n] = {
            id: e
        }, a && function(e, t, r) {
            const a = ls([e, t]);
            ac.addSchema(r, a)
        }(t, r, a)
    }), {}), sc.value = !0
}
var hc = {
    props: {
        isMobile: Boolean
    },
    name: "LoginButton",
    methods: {
        async getSteamSignLink() {
            const {
                link: e
            } = await uc("auth", "steamLink");
            e && window.open(e, "_self")
        }
    }
};
hc.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", {
        onClick: console.log("nwu")
    }, [wa("img", {
        src: "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAALQAAAAjCAYAAAA9riDJAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAIGNIUk0AAHolAACAgwAA+f8AAIDoAABSCAABFVgAADqXAAAXb9daH5AAABycSURBVHja7Jx7cFT1/fdf576X7CbhbiBEIARRbmp4lFoQ6APiBbF4oQWZ/lrn13Z6fayPU7Haqc60dvQZO9Nqx7bWaTsqavvrj7GKgtQRHxsBuYiJqVGSECKB3Mhms9ndc3/+2JzD2c0mogSnncfvzM5mz37O93y/n8/7c/1+NoJt2wC4rrsaWA1UMTRc16XYKHb9bGk/6bVzRTMW95zN50/r3nP93bmkG/q7Ddi5YMGCnQCybdu4rvufr7zyyu319fU1pmlKfDY+G/8mQ5Zle9q0adcYhvGL2tra38mWZa3euXPn7YcOHZr7GXvO7XBdF9d1cRwn710QBARBQBRFBEHIow2+vOHRBOmL3ePRei9Jkvy/i60nSCuK4hnNOdJ6C9cafA+u+WyHbdtSc3PzXMMwbjcMo022LGv14cOHaxzH+Qxx5xjMtm1jWRaGYWCaJpZl4TgOoigiSRKKoiDLMoIg+LQeTRAooigiiiKyLCNJEqIo4roulmVh2zZDXtcHkCzLKIqCqqrIsuyD1XuGaZo4jpNH663Dm9d7AUiShCzLeXM5jpM3l+u6/jo9xfOUyrs2lqO9vb1m1qxZq2XLsqoMw/gszPgUwGwYBplMxn+ZpukLXtM0NE1DVVUkScKyLHRdJ5vNYpqmD1IPFIqi+PSiKPqKouv6MFpVVQmFQkQiEUKhELIs47ouuq6TTqfJZDJYloUoisPobNtG13UymQy6ruM4DoqiEA6HCYVCKIoCgGmaefsCUBQFRVGQJMkHsqcsnrcYq+E4jmQYRpXsWYCxFF4xN1vMRZ7pfN76Ct3cmdxXaNXGejiOk7e+Ynt0HAfDMBgcHCSVSlFdXc0NN9zAhRdeiKZpZLNZjh49Sl1dHfv27WNwcJBFixZxzTXXEIlEfOvo7cWzjrqu89JLL1FXV0dlZSUbN26kvLwc27aHhQ89PT08/vjjPtgsy2JwcBDHcdiwYQO1tbUcPXqUZ599lr6+vjzrnE6nqaysZMOGDbiuy3PPPUdTUxOlpaX+mjKZDP39/VxyySV88YtfJBQK8dBDD9Hb28uKFSsYN24cXV1d1NfX+3wZa3kYhsGYATrocrzKiSdc13Xz3NSZgjro7hzH8e+XJGlUcHlg9u71LJqqqmNqFVzX9cMH27ZRVdW3QAVxng/ouXPncs899wCQSCTo7e1FURSqq6uZNm0anZ2dvPvuu0iSRDweJxwO4zgO8XgcWZZxHIdEIoEoiui6jiRJZLNZXNelqqqKcePG+VY36Oo9Gi9sMAyDVCpFRUUF1157LQCTJ0/m8OHDvPLKK77ltW2bTCYDwPnnn4+qqqxfv54tW7b4oQ5AKpXCtm2WLl3KzJkz/Wecd955JJNJ4vE4qqr6IdG5MC66riMHAXi2gs1kMqTTaS644AIGBwfp6OhAEARuueUWGhoaaG1tRVXVvHs9pgRjPi+mdBwHXdepqqrioosuYtu2bXmACdJ6G9J13QeYZVncd999PPvss7S0tFBSUuLTes8sTGqClq3Q2wRpPeXJZDLMnDmTW265hfvuu49IJEIkEvFdrGcNPf6sW7cOgO7ubr797W/T1NREVVUV119/PaZpcvjwYRRFobGxkYceeohMJkNPTw/33nsvCxYs4Pjx49xxxx2Ul5cTiURIJpO+wniG6cknn+SFF14gGo36IYSiKBiGQSgUwjRN0uk0uq5TW1vrGwNBELjssst44403SKfTiKLoy8AwDJ8f1dXV1NbWcvDgQZ83yWSSxYsXc+mll+YpcltbGxUVFTQ3N/sW3XGcvDh/TC20F8edZaZJNpultLSUX/7yl3R3dxONRmlqauLhhx9m6tSpdHR0UF9f78dlgbJLXtIjSRKhUAhN03yQjhs3jqlTp9Lf3+/HZMVo0+k0AL/+9a9Zv349rusye/ZsRFGkt7cXy7J8hQp6EQ90XjwbjO+CFt0DuW3bfvKTyWSQJInZs2fT29tLNpvFtm1CoZAfDwcVNvh8L2Y9ceIETz31FLFYjGg0iizLmKZJZ2cn/f399PT0MDAw4PPj6NGjpFIpSktL/VAq6GXb2tpoa2tDFEVKSkqIRqPE43FisZhvpbPZLPF4nNWrV5NOp9m3bx8zZ85k4cKFzJ49m0OHDqEoCoIg5CWEAJqmsWHDBt58802SyaTPm5UrV+Z5T0EQGBgY4PDhw1RWVtLc3OzPOdrZxVlb6LMNOTwBX3HFFXR3d3PzzTcTDoeZN28e2WyWzs5ONE0jkUiwbNkyVq1aRUtLC/PmzeMHP/gB3/ve9zh58iSzZs1CEASefPJJMpkMqqpimibt7e0sXbqURCLBHXfcUZRWlmXS6TQPPvgg4XCYhx9+mNtuuw2AmTNnctVVV9HW1saf/vQnFixYwOc//3nS6TSDg4P85S9/YfPmzVx00UU0NjbyxBNPcPHFF3Prrbdy1113sWDBAjZt2sRdd91FaWkpa9euZeLEiaRSKTo6Ojh27BgA69evZ+nSpezevZs333wzz9J7Cdorr7zCnDlzmDJlCn/4wx/YsWMHDQ0NNDc309HRQSgU8hU9HA5jmibhcDhPwcLhMJFIhHA47CthcKxatYqysjKi0SiaphEKhdi1a5evuF6yuWjRIsaNG0dDQwOPPPIImzZtYvr06Vx++eUcOHDA52vQALmuS39/P+effz4rVqxg+/btACxbtowlS5YwODgIQDQa9fds2zZdXV0oijKsHDjWFlr0XNXZvLyFHTx4kAkTJvDiiy9y5513cvLkSbLZLFVVVYTDYZLJJN/5zndoampC0zTmzJlDX18f06dPZ8WKFezbt485c+awevVqP/O2bZtIJMKcOXNIpVIj0nplsD179gCwdetWX1FnzZrFgQMHWL9+PdXV1ciyzOrVqzFNk3feeYdNmzaxbNkynnnmGZYuXcqtt96KLMvU1NSQSCRQFIXZs2fT19fH1VdfzaWXXsq+ffuora0lHA77Ai8pKeHIkSNs3ryZwcFBPwzwAK2qKrt27eLRRx/l8OHDhEIh1q1bx49+9CN+8pOf8OUvf9lXYq88FiyhecOrHnhls8K8YPny5dx5551861vf4rbbbmPTpk2UlJT4eUU2m0UQBG666SYA6uvraWpqYu/evRiGwZIlS5g+fboflnj7EwQBXdd5+umn0TSN66+/3t/j9ddfTzqd5h//+Ac9PT15iXhh+S4Yso3la8wstGclGhsb+f73v8/KlStZtWoV8+fPZ+PGjf4GVq5cSSQS4YEHHmDt2rVcd911ZDIZXNelrq6Op59+mquvvhrHcfw4OBhreXFcMVov4WtqagJg+/btvvt7/vnneeGFF/j617/uVw0AHn30UURR5Ktf/Sq7du3i+eefp6amhoULF9LQ0ODHhrqu+yHNvHnzqKur449//CNr1qzJszQPPvigvy8vWQxWQby4etu2bbz66qtUVVX5Sjljxgy+8pWvYBgGL7/8cl64MtIBTbGDDIAXX3yRAwcO+CGNqqr09fX5sXI6neb888+nurqaTCZDb28v1dXVAPT09FBRUcEll1xCc3Mz2Ww2L9ywbZvXX3+dFStWUF1dzbXXXktrayu1tbVs376dV199lQULFhTNPYJhxlhbZz+GDiYTZ1Ph8Fy7JEn84he/AGDdunV5SdahQ4dIp9P88Ic/zEsKveTOc61BLQ4yxLNUxWiD5SyAqVOn0tvbm+e+g0koQCgUQhRF2traWLhwIZIksWjRIlpaWnxlmDRpEnPnzvUB+c4777BkyRLWrl3LpEmT8tYXiUTyEtZilsh79okTJ/jggw/YuXMne/bs4f7776eyspLq6mrfTRdLTEc7FfTGq6++yo4dO5AkiWg0SiQSIRqNoqqq7/WuueYaAMLhMJs2bWL9+vWoqkp5eTkAa9euZefOnXR3d+cZFVEUGRgY4NFHH+WRRx7htttuo7u7m3Q6zfPPP8/AwICfJwR5EJTnuRq6ro8doF3XpaamhjVr1vDzn/+cY8eO8fjjjxOJRPxYKpVK8dhjj7FmzRo/1gqFQv4JVSwWyzsFC55KeS7d+66Q1pujqamJ3t5etm7dyu233+4nYvF43HfX3ohGo4iiyDPPPMN3v/td9u3bx8GDB3nqqafo6enhvffeY/v27X6cGIlE+POf/8zkyZP9aoUgCP6csVjMF6bnMTwge1WXK664gnnz5vHGG2/wwQcfIAgCixcvZty4cQD09fVhmiaapg2rvBTWb4MKEvy+pqaGpqamvBhakiROnDiBaZqUlZWxcuVKbNumpaWFjo4ONE3DNE3i8Tg1NTWMHz+eiy++mJdeesk/zQxa6f379/PWW2+xePFipkyZwt///nf27NnD4sWLhxmrTwPMANlsNgfosSjbAbz22mvs2LED0zT9akFZWRk//vGPcRyHaDRKZWUlzzzzDCtWrOCf//wnsViMLVu2oKoqsViMe++91z9+9UB68OBBbr75ZsrLy7nnnnsQRXFEWl3X+cY3vuFbuJtuuglRFCktLeXmm2/217phwwbC4TCiKGIYBj/96U+xbdtXoPLycu6++25M00QQBH73u99RUlLC5MmT6ezspL29nYsuuogjR46wd+9ebrzxRkpLSzl06BBf+tKX0DQNURSxbTuvJr5hwwYqKytZunSpH8qUlJSgqirHjx9n9+7dPkALQxUPJIWlx6BSA2zevJkbb7zRpxMEgRMnTnD33Xfjui6rVq1C0zROnjzJz372Mz788ENkWcayLARB4P777+fyyy/nuuuuY//+/XR3d+fVtGOxGIlEgq1bt7J48WISiQQvv/wymqYRi8WGeVSvMnQuwozgSCaTY2Ohg5bKO8YNJgGeVnuWeuPGjXR1dfHII48Qi8XQNC3vMCLYHOOV0Aq/L6T1BFsYe45UVw6eonlHs5419J6taVoebxzHYcKECVRUVLBw4UKeffZZ3nrrLd8yB62Yt/dgDA3wm9/8hmXLljF//nymTJniW+XXX3+dv/3tb3R1dRGJRPJCMVVV6ezspLm5mePHjw/boxeitLa20t/fn3dw4c3hlddUVWXu3Lm0tbVRX19PW1ub3+PhJX11dXVMmjSJsrIyJk+eTH9/P6Zp0tzcjOM4aJpGPB6ntbWV3/72t2SzWerr6yktLcVxHI4ePeonk57cPg0rnUwmEf7617/++cUXX7zpXLsDz0p5Bx+eAnhgHssTvHPZj2Gapi8sSZLy+i9G27t3bzabJZvNYhjGsGYfr6Ye5Elhj4bXm+GB0EuGgvMW6/sI5hee1/AMhaeMwZPPYNNUYdgQrNMXhjxBBfbk650dnGsZJxKJv8hew8mnAQjP2ngxZ7BT7Fy7o7EYHgCCNWEPyKPxsLBRyPNi3j0ecLzwKVirDT4zmPwGk1tPsbz3Yj0swbClcE1BOXhrLOyfCYI3GH4EAT1a/8ynIeOBgYHiIcfHffDH0bxCS/bvAuZCUH+SPQS7zUbqLw4mUoXhy0j8DrZlKooyYj9yMTkVXj8TS1rsFDVotArn/rSSwoGBAfIsdOHPW4r99KWQsSNt7rMxMhhG49VIylEMPMVygk/qPYspwZkWAz5qneeq7lw4UqnUaQvtxYheeSlYMvIahQobeQoz78L2yf/fQD5SM9NH0Re67o8LwmKgKbTwo7Xujgbos1GSYPhRbF0eXsaq825wcDBnoQ8ePOgDunARoiQhjGKxCy1E4WskLS5WXz1TsPyrKMpIwirs2jtTQJ6pRS8mh8IQprCGXQw4xdYQlE2Q1x/XGxQeJI22t0/SJ19spNNp5EwmIwQL/4ULKDyxsm0Fy1JwnOFaJcsmiqKf0YaLxXbBktlowioWZ34UsILPNAwV05SRZQtFsRBFZ0gIIqYpI0kOsmyNCiLHAcuSsW0BWbYQRWuok03CshQUxUJR7GEJlBfe5Y7sJRxHRBTNoTUImKaCbStIkoUkmUhSPrhGAvNIPDBNFcdREQQRSRJRVRtByD1bFA0EwRjR6IykSEEZFCquaSrouogo6oiiecaAHi1POFOwZzIZ5MHBQemj+lOD1y1Lobf2m5iR8cPoxh/eipRuRBSdj4yZvE0E+wSKWfYzYXYxQRezULnvJFJaFV21G4j1vEf4xGFCg0eRJBPbFkhUr0NJdRLreh1ZtooqVY4PKslpX8AomUT5u0+hKNZQ3TlM74KvEDlZT0nvm8iyOexkLwd8hcGKKzFKJlPW9ByKomNZCgPTryJVcTGhUy2UHNmFrJ9CUQzg48egpqmSnrqc5PQlOJKKrA8w4e0/IllJeudvJtJZT0nvHgTBGMbfYkmcV13xSoOFP9Z1HJlUbC5981YwYe+v0DT3jMKmYDg7UuJaTJGKnhT29/cLH+UaCq3w+P2P4Tgi2VkrsUKllLz73/53hh3GdQVE0UGWTSxLAVwcR0IUHRxHRBBy39m2gutquK6AJFlD16Sh6wKybCIIDpalIAg5Cxq85roiomgjSRaWpebRePd7SpizeBaO42JFNLRkB0Kmn96aa5D1AcrffgJZzhJp/HOOTrJIpxUcR/Hn9Oby9uoCgqUPWeUSZNnEcYb+z4kSwrYFDCOfH6Ioo+sCriviyKGiPI50NeLIIbqWfId4+15ix14GckqQW4fgz+l5S0FwkSRzCPw5PuixGpLTl1De8F9IfUcRBAdRsjEtBRdw5BCGISPL7rB5RDF4Lbd2XfdkWTJMlrm9u9iOg1tgiBxH9D27x7tia5ckC9tWsG0ZQXCRZRNJMoeBO9i9Fxy6riMPDAx8rOAl92ATy1LJBkAuig6Z6Bz65t2II6ko6V7K3n6aRO1GREtHj1egpHsxI+OR9AEm7PklpxZ/E1uL4Ugqob5WyhuexIhX+3PE2/ciD5ygf9YXEG0DMzKe8vd3IGZOkbjgOmwthpbsIPrhvmE0mYk1lDc8mTuJm3cr4e73ifbUIQg5RltajLKWXYRbdpG4+Kv0z99E+btb6Vv0H4R7PyDasZvUrHVkSqdhRsYzse5XmOctIDHjSgDi7XtzTIxPJb18CwDjGreh9jScZnCsZhg/nPAEEhfn1g5QcuLtYdbXkUOUNT1HpG0q/RfeAKxByiRIVn2OCXt+SWbm/8QKlRL94BUStRsxI+MRbSMH3CEP6Tgy5riZSPoAUt/RITC4mGI53cu/O7T2CpTJ83w5BecRB3v8a5I+QHn9c/RfeMOIsvQUXmA4nGxbITHnFtITL/D5JCXa855Z1rQdMd1LuvoKskPrHr//sWGADuZ6hbV1ADGVSrljkWhZlkJy9mpKOg4Rb9+LrcVw1QiOpGJGJ1By4m0cSaX8/R3YWgw7OiUH5FMtTKz7FUZ8Kka82p9jwv7fk6y8DFcOY2sxop0NaMkOXCVE4oLriHY1Mq5xG9YQMAppsuUz0MfPxwxXYMSnIve8jygO71lRFIN4w3+RKZ+BKcZO1zRn5sBc2riNSa89gKtGSMy4knGN24i378UKleYYaBtMrPsV8fa99M/6Aq57mo/F+JGacSXhU81Meu0BtGQHoqUzEutDRjslH+4nM74aVwkh6wO+QgJkZixF0pM5gOgD2PEKHEcaMjwWamdOubqWb6Fr+Rb6Fn0Nyer3n13Wupvx+x8rOs/g7FWIls6k1x7wlW80WbruUEhXoJyWpZCeeiV6fCoT9v8eLdmBEy7Pmz90qgUrdh79F96AI2tMfOP/MH7/Y76SjFZFGfYvHlKp1Cc83HARrSy2FsdxxFxCFRnP4KQL/UXJ6ZOItkH82JvI2X5kfQD1xAFE28COT8t9TnUimkkES8dVwpiR8aidDYipLt91S/oA2rE3cmFB7xFsLUao+dV8zxGgiRzfTaT7PQan/Q+MyfMInWpBcfrywFAIDgBXjfgKIve1Ilo6py7ejFH1Oazx1WjJjjwLDKAMdqM4faidDTnQuqctRiE/pMFOzOgEQscP5Nypniwe1mX789bmSGrxGDk6iWz5DLITL6C0cRuh9jd85bAsBTHVxfj9jzHptQeYsP/3WFqMbOXSAsV2h82jHXsDPT6V6If78q3fKLL0MOCEy/N467oiRslkol2NyOkTp73X0PyiaGNrcUQrS7j3CLYW59Tib2CWzvzIvKFYC62YSqXOujDvuTPRNoh2NRJpeonMzC+Qmn0tjqQiZvoQM31DYHFzViBcdtolRafgyhqCmfEZZFZcgmgbiJk+n05VswhG7neDTkmuF9mVtbx1aFoGSTKJtP0DMzqBZOVlRNr+Mcx1ObKG40gYRojkvBvRkh1IgydPP6ungdKDf6SsaTuJGVcimFksLeZbQGfouY6sYVkKxuR5KOlev2LiASDIj8Gaa5D0AYzJ87AsBTM6sXjJS9YwTZWsWklqWi3RrkYEM+uv2ee5raMlOyh5979xIuPprf2mH6dalkLX8i0YEy4aMgyR3JoyfYiig6QnceQQguAOm+fU4m8i2gZOuBxXLUG0DVwlMqosg4qci5slMpmSnGJZWaxQaYB3IX9+s3QWerwCMdNHuOXvlO/7LeHeI6RmXOnv5eMAWk6n0+7ZnOYItp4Ds2gSP/YmiRlXkqy8DCXdS2njNvTSyhydmcmzan5DyYwrYcaVRLrfI5Q6QlnTdk5deAMAZa27CyojoNoJ4u176am97bRbi51XQOegZo8TOtWSA2f2OKLinFa8dK/vigF/rYKQA6FgZulb9DX0eEUuSet+D+3kW8hT5vv3iLaBmurKWbblW5D0Acree8G3KoKZLcoPte8oiTnXkKy8DNE2sEKlfpgiirafM6SGnhPqayV6dCeWVIZT9Tn/+SUn3ibccYjEBdfRtXyLH4d6blqWTeLte3O8vPAGRNugpOMQkcQ7eConWllE0SZ6bM+weYDcvUM5gzluJqJtjCpLQXARzCx6vMJfJ8CE/b+nb/4tfq4h2Dqxo/+XUxfegKwP5BRGDtP9+f/te6Oy1t1IkjVqC0WxypxQXV39V9u2v/hRDTYjxc2OIw0lhTamqflaFaxy5KoO+H87jojrivQt+hrh3g9Q2+qGkk0D21axbcVPQL1s2MukXRdMU/NpPOHZtuTT5Eo4EXou/x5l771AZChRCiYpwVq6t1ZvT7l1y75F8fbn7dcTXq66ogx9doYqMKerEV7FxgOrJJm4ruhXcbw5vH16z/cqOF4s7PEseL2w2lNY5cjVtNXA+nLfy7KB4whDtenTMiqcB4Q8C5lbgzRMlt49Of65eRgolE9wT64r4DgSZsUl9NVcxcS6XyGaA75ye2caHwXoYGTR2tr6FzmdTrdFo1HbNE1ptMOKkUp4YAYSLB1ZzhY0zZi+9ZckY2gxYBiRwH3ZIWG7yHIGWc7khUH5yYGLomRRlGxejTLwQxRsW8Y4rxbRNlD6WxA1p2ilZqQqTvA9/zurCA+yw66pqjkEYtNfZ/49+ojhXVAp872OXfT6yImTi6LoeaA43Z0HsmwEuveKP7Pw3uCac2B2h50mynLW50nwTMGTT65FNZLnAePte5HtPhQte8YHKd6PEU5jS7KBNjmbze5QVXWN67oXjFXzzce57lmTM43hz+zfgInY4TLCvUdGdVvncr//qo1RozUWfdx9Fuv6O5P+Flk2KX/7iTwPqKgGUPz+0Z7tzT84OPg+sFOoqqoSurq6vl5eXv6/VFWd7QSzjnM4bFvGttVRreVZiC6viP9JTtk+G/8avTJn0EJhZzKZ97u6un5RVVX1O6GqqgpAaG9vXw2sAaoEQRAFQRABURgagDCUPQ4dBLmu67qO67pO4LP7L4Aewfe5pz9/huh/z+FhDw9jRWjagJ1VVVU7Af7fAAMtKuLyer2SAAAAAElFTkSuQmCC",
        class: ["steam-login", {
            "login-mobile": r.isMobile
        }]
    }, null, 2)])
};
var pc = {
    props: {
        routes: Array,
        isMobile: Boolean,
        logged: Boolean
    },
    computed: {
        links() {
            return this.routes.filter((e => "/changelog" !== e.to))
        }
    },
    components: {
        LoginButton: hc
    },
    setup() {
        const e = Da(xo),
            t = Ja((() => e.currentRoute.value.path));
        return {
            isActive: e => e === t.value
        }
    }
};
pc.render = function(e, t, r, a, n, o) {
    const i = ta("router-link"),
        s = ta("LoginButton");
    return ha(), fa(ia, null, [wa(i, {
        to: "/",
        id: "logo"
    }), wa("nav", {
        class: {
            "mobile-visible": r.isMobile
        }
    }, [(ha(!0), fa(ia, null, en(o.links, (e => (ha(), fa(i, {
        to: e.to,
        class: {
            active: a.isActive(e.to), on: e.className
        },
        key: e.path
    }, {
        default: Vt((() => [Pa(u(e.text), 1)])),
        _: 2
    }, 1032, ["to", "class"])))), 128)), r.logged ? _a("", !0) : (ha(), fa(s, {
        key: 0,
        class: {
            "login-visible": r.isMobile
        },
        isMobile: r.isMobile
    }, null, 8, ["class", "isMobile"]))], 2)], 64)
};
const fc = Ze(localStorage.getItem("last_route") || "/");
yr(fc, (e => {
    localStorage.setItem("last_route", e)
}));
const mc = {
    logged: Ze(!1),
    loaded: Ze(!1),
    data: Be({
        session: {}
    })
};

function vc(e) {
    mc.data.session = e, mc.loaded.value = !0, e && e.user_id && (mc.logged.value = !0)
}
const gc = e => e ? `https://cdn.cloudflare.steamstatic.com/steamcommunity/public/images/avatars/${e.substr(0,2)}/${e}_full.jpg` : "",
    yc = e => `https://steamcommunity.com/profiles/${e}/`;
var bc = function(e = {}) {
        const t = Be([]),
            r = function() {
                const e = function*() {
                    let e = 0;
                    for (;;) yield e += 1
                }();
                return function() {
                    return e.next().value
                }
            }(),
            a = new Map,
            n = e => {
                const r = t.findIndex((t => t.id === e));
                a.has(e) && clearInterval(a.get(e)), -1 !== r && t.splice(r, 1)
            };
        return {
            list: t,
            addNotify: o => {
                const i = {
                    ...e,
                    ...o
                };
                i.id = r(), t.push(i), i.timer && a.set(i.id, setTimeout((() => {
                    n(i.id)
                }), i.timer))
            },
            removeNotify: n
        }
    }({
        timer: 5e3
    }),
    wc = {
        name: "Notifier",
        setup() {
            const {
                list: e,
                addNotify: t,
                removeNotify: r
            } = bc;
            return {
                list: e,
                addNotify: t,
                removeNotify: r
            }
        }
    };
const Ec = {
        id: "notifier"
    },
    Pc = wa("div", {
        class: "left"
    }, null, -1),
    kc = {
        class: "right"
    },
    _c = {
        key: 0,
        class: "title"
    },
    Sc = {
        key: 1,
        class: "content"
    };
wc.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", Ec, [(ha(!0), fa(ia, null, en(a.list, (e => (ha(), fa("div", {
        class: ["el", e.type],
        key: e.id,
        onClick: () => a.removeNotify(e.id)
    }, [Pc, wa("div", kc, [e.title ? (ha(), fa("div", _c, u(e.title), 1)) : _a("", !0), e.content ? (ha(), fa("div", Sc, u(e.content), 1)) : _a("", !0)])], 10, ["onClick"])))), 128))])
};
var Cc = {
    props: {
        show: Boolean
    }
};
const Tc = {
        key: 0,
        class: "loader"
    },
    xc = wa("img", {
        src: "/logo.svg",
        class: "logo"
    }, null, -1),
    Dc = wa("img", {
        src: "/icon/loader.svg",
        class: "animation"
    }, null, -1),
    Oc = wa("span", null, "Loading...", -1);
Cc.render = function(e, t, r, a, n, o) {
    return ha(), fa(Pn, {
        name: "fade"
    }, {
        default: Vt((() => [r.show ? (ha(), fa("div", Tc, [xc, Dc, Oc])) : _a("", !0)])),
        _: 1
    })
};
const Rc = [{
    to: "/",
    text: "Browse",
    login: !1
}, {
    to: "/profile",
    text: "Profile",
    login: !0
}, {
    to: "/report-user",
    text: "Report",
    login: !0
}, {
    to: "/faq",
    text: "FAQ",
    login: !1
}, {
    to: "/changelog",
    text: "Changelog",
    login: !1
}, {
    to: "/contact",
    text: "Contact",
    login: !1
}, {
    to: "/feedback",
    text: "New Feedback",
    login: !0,
    className: "green"
}];
var Fc = {
    name: "App",
    components: {
        Loader: Cc,
        Notifier: wc,
        Menu: pc
    },
    data: () => ({
        isMobile: !1
    }),
    setup() {
        const e = Be([]),
            t = t => {
                e.length = 0, Rc.forEach((r => {
                    (t && r.login || !r.login) && e.push(r)
                }))
            },
            {
                loaded: r,
                logged: a,
                data: n
            } = mc;
        return yr(a, (e => t(e.value))), {
            loaded: r,
            logged: a,
            data: n,
            routes: e,
            getRoutes: t
        }
    },
    async created() {
        if (await dc(), "/login" === this.$route.path && this.$route.query["openid.ns"]) {
            const e = document.location.href;
            vc(await this.$callApi("auth", "steamVerify", {
                url: e
            })), await this.$router.replace(fc.value)
        } else await async function() {
            vc(await uc("auth", "me"))
        }();
        "/login" === this.$route.path && mc.logged && await this.$router.replace(fc.value), this.getRoutes(this.logged)
    },
    methods: {
        handleMainClick() {
            this.isMobile = !1
        },
        handleLogout() {
            !async function() {
                await uc("auth", "logout"), mc.data.session = {}, mc.logged.value = !1
            }(), this.$router.replace("/")
        },
        getAvatarPath: gc
    },
    watch: {
        $route() {
            this.isMobile = !1, this.$refs.scroll && (this.$refs.scroll.$el.scrollTop = 0, setTimeout((() => {
                this.$refs.scroll.update()
            }), 500))
        }
    }
};
const $c = wa("div", {
        id: "popup"
    }, null, -1),
    Ac = {
        class: "hamburger-wrapper"
    },
    Mc = {
        key: 0,
        id: "profile"
    },
    Lc = {
        class: "username"
    },
    Nc = wa("img", {
        src: "/icon/gear.svg",
        class: "settings"
    }, null, -1),
    Ic = wa("span", {
        class: "hamburger-box"
    }, [wa("span", {
        class: "hamburger-inner"
    })], -1);
Fc.render = function(e, t, r, a, n, o) {
    const i = ta("Loader"),
        s = ta("Notifier"),
        l = ta("Menu"),
        c = ta("router-link"),
        d = ta("router-view"),
        h = ta("perfect-scrollbar");
    return ha(), fa(ia, null, [$c, wa(i, {
        show: !a.loaded
    }, null, 8, ["show"]), wa(s), wa("header", {
        class: {
            "mobile-visible": e.isMobile
        }
    }, [wa(l, {
        isMobile: e.isMobile,
        routes: a.routes,
        logged: a.logged
    }, null, 8, ["isMobile", "routes", "logged"]), wa("div", Ac, [a.logged ? (ha(), fa("div", Mc, [wa(c, {
        to: "/profile"
    }, {
        default: Vt((() => [wa("img", {
            src: o.getAvatarPath(a.data.session.avatar),
            class: "avatar"
        }, null, 8, ["src"])])),
        _: 1
    }), wa("div", {
        class: ["wrapper", {
            "mobile-visible": e.isMobile
        }]
    }, [wa("div", Lc, u(a.data.session.username), 1), wa("div", {
        onClick: t[1] || (t[1] = (...e) => o.handleLogout && o.handleLogout(...e)),
        class: "logout"
    }, "logout")], 2), wa(c, {
        to: "/settings"
    }, {
        default: Vt((() => [Nc])),
        _: 1
    })])) : _a("", !0), wa("button", {
        class: [{
            "is-active": e.isMobile
        }, "hamburger hamburger--spin"],
        onClick: t[2] || (t[2] = t => e.isMobile = !e.isMobile),
        type: "button"
    }, [Ic], 2)])], 2), a.loaded ? (ha(), fa("main", {
        key: 0,
        onClick: t[3] || (t[3] = (...e) => o.handleMainClick && o.handleMainClick(...e))
    }, [wa(h, {
        ref: "scroll"
    }, {
        default: Vt((() => [wa(d, null, {
            default: Vt((({
                Component: e
            }) => [wa(Pn, {
                name: "fade-fast",
                mode: "out-in"
            }, {
                default: Vt((() => [(ha(), fa(aa(e)))])),
                _: 2
            }, 1024)])),
            _: 1
        })])),
        _: 1
    }, 512)])) : _a("", !0)], 64)
};
var jc = {
    setup(e) {
        const {
            img: t,
            className: r
        } = e;
        return {
            src: `/icon/${t}`,
            style: ["icon", r]
        }
    },
    props: {
        className: String,
        img: String
    }
};
jc.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", {
        class: a.style
    }, [wa("img", {
        src: a.src
    }, null, 8, ["src"])], 2)
};
const Uc = {
    required: "This field is required",
    minLength: "Minimum characters: :limit",
    maxLength: "Maximum characters: :limit",
    type: "Wrong type",
    format: "Wrong format"
};

function Hc(e, t = {}) {
    return ((e, t) => {
        const r = /:(\w+)/g;
        let a;
        for (; a = r.exec(e);) e = e.replace(a[0], t[a[1]]);
        return e
    })(Uc[e], t)
}
var qc = {
        props: {
            name: String,
            placeholder: {
                type: String,
                default: null
            },
            readonly: {
                type: String,
                default: null
            },
            disabled: {
                type: Boolean,
                default: null
            },
            icon: {
                type: String,
                default: null
            },
            type: {
                type: String,
                default: "text"
            },
            validator: {
                type: Object,
                default: null
            }
        },
        data: () => ({
            errors: !1,
            edited: !1
        }),
        computed: {
            value() {
                return this.validator && this.validator.data[this.name]
            },
            error() {
                return !(!this.errors || !this.errors[0]) && Hc(this.errors[0].keyword, this.errors[0].params)
            },
            isEdited() {
                return this.checkErrors(), this.edited || this.validator?.force_validate
            },
            style() {
                return this.disabled ? "disabled" : !!this.isEdited && (this.errors ? "error" : "validated")
            }
        },
        methods: {
            checkErrors() {
                this.validator && (this.errors = this.validator.getErrors(this.name))
            },
            handleInputOnce() {
                this.edited = !0
            },
            parseValue(e) {
                return "number" === this.type ? "" === e ? null : Number(e) : e
            },
            handleInput(e) {
                this.validator && (this.validator.set(this.name, this.parseValue(e.target.value)), this.validator.validate(), this.checkErrors())
            },
            handleIconClick(e) {
                this.$emit("iconClick", e)
            }
        }
    },
    Yc = "/icon/warning-red.svg";
const Bc = {
        key: 0,
        class: "error-text"
    },
    Wc = wa("img", {
        src: Yc
    }, null, -1),
    Vc = {
        class: "input"
    };
qc.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", {
        class: ["input-wrapper", [o.style]]
    }, [o.isEdited && n.errors ? (ha(), fa("span", Bc, [Wc, Pa(u(o.error), 1)])) : _a("", !0), wa("div", Vc, [wa("input", {
        placeholder: r.placeholder,
        name: r.name,
        onInput: t[1] || (t[1] = (...e) => o.handleInput && o.handleInput(...e)),
        onInputOnce: t[2] || (t[2] = (...e) => o.handleInputOnce && o.handleInputOnce(...e)),
        onPasteOnce: t[3] || (t[3] = (...e) => o.handleInputOnce && o.handleInputOnce(...e)),
        readonly: r.readonly,
        disabled: r.disabled,
        onBlur: t[4] || (t[4] = t => e.$emit("blur")),
        autocomplete: "off",
        value: o.value,
        type: r.type
    }, null, 40, ["placeholder", "name", "readonly", "disabled", "value", "type"]), r.icon ? (ha(), fa("div", {
        key: 0,
        class: "btn-search",
        onClick: t[5] || (t[5] = (...e) => o.handleIconClick && o.handleIconClick(...e)),
        disabled: n.errors
    }, [wa("img", {
        src: r.icon
    }, null, 8, ["src"])], 8, ["disabled"])) : _a("", !0)])], 2)
};
const zc = {
        1: {
            name: "bitcoin",
            short: "BTC",
            icon: "/icon/payment/btc.svg",
            position: 1
        },
        2: {
            name: "ethereum",
            short: "ETH",
            icon: "/icon/payment/eth.svg",
            position: 2
        },
        3: {
            name: "litecoin",
            short: "LTC",
            icon: "/icon/payment/ltc.svg",
            position: 3
        },
        4: {
            name: "USDT",
            short: "USDT",
            icon: "/icon/payment/usdt.svg",
            position: 4
        },
        5: {
            name: "PayPal",
            short: "PayPal",
            icon: "/icon/payment/paypal.svg",
            position: 5
        },
        6: {
            name: "Cash APP",
            short: "CASH APP",
            icon: "/icon/payment/cashapp.svg",
            position: 6
        },
        7: {
            name: "venmo",
            short: "Venmo",
            icon: "/icon/payment/venmo.svg",
            position: 7
        },
        8: {
            name: "zelle",
            short: "Zelle",
            icon: "/icon/payment/zelle.svg",
            position: 8
        },
        9: {
            name: "bank wire",
            short: "bank",
            icon: "/icon/payment/bank.svg",
            position: 11
        },
        10: {
            name: "cash",
            short: "Cash",
            icon: "/icon/payment/cash.svg",
            position: 10
        },
        11: {
            name: "swish",
            short: "swish",
            icon: "/icon/payment/swish.svg",
            position: 9
        }
    },
    Xc = {
        440: {
            name: "Team Fortress 2",
            short: "TF2",
            icon: "/icon/game/tf2.svg",
            position: 3
        },
        570: {
            name: "Defense of the Ancients 2",
            short: "DOTA2",
            icon: "/icon/game/dota.svg",
            position: 2
        },
        730: {
            name: "Counter Strike: Global Offensive",
            short: "CS:GO",
            icon: "/icon/game/csgo.svg",
            position: 1
        },
        433850: {
            name: "Z1 Battle Royale",
            short: "Z1",
            icon: "/icon/game/z1.svg",
            position: 4
        }
    },
    Qc = {
        1: {
            name: "Item sale",
            icon: "/icon/item_sale.svg",
            phrase: "Sold",
            trade_type: "item"
        },
        2: {
            name: "Item purchase",
            icon: "/icon/item_purchase.svg",
            phrase: "Bought",
            trade_type: "item"
        },
        3: {
            name: "Balance sale",
            icon: "/icon/balance_sale.svg",
            phrase: "Sold",
            trade_type: "balance"
        },
        4: {
            name: "Balance purchase",
            icon: "/icon/balance_purchase.svg",
            phrase: "Bought",
            trade_type: "balance"
        },
        5: {
            name: "Middleman",
            icon: "/icon/middleman.svg",
            phrase: "Assisted trade of",
            trade_type: "item"
        }
    },
    Gc = {
        0: {
            name: "Neutral",
            icon: "/icon/neutral.svg",
            position: 2
        },
        1: {
            name: "Positive",
            icon: "/icon/positive.svg",
            position: 1
        }
    },
    Kc = {
        1: {
            name: "Scam"
        },
        2: {
            name: "Other"
        }
    },
    Jc = {
        1: {
            name: "I went first",
            icon: "/icon/trade_first.svg"
        },
        2: {
            name: "I went second",
            icon: "/icon/trade_second.svg"
        }
    },
    Zc = {
        1: {
            name: "Active"
        },
        2: {
            name: "Looking to trade"
        },
        3: {
            name: "Inactive"
        },
        4: {
            name: "Retired"
        }
    },
    eu = {
        1: {
            name: "Fake feedback"
        },
        2: {
            name: "Spam"
        },
        3: {
            name: "Harassment"
        },
        4: {
            name: "Missing information"
        }
    },
    tu = {
        1: {
            reason: "scamming"
        },
        2: {
            reason: "impersonating"
        },
        3: {
            reason: "banned alt account"
        },
        4: {
            reason: "sharking"
        },
        5: {
            reason: "other reason"
        }
    };
var ru = us((function(e, t) {
        e.exports = function() {
            var e = "millisecond",
                t = "second",
                r = "minute",
                a = "hour",
                n = "day",
                o = "week",
                i = "month",
                s = "quarter",
                l = "year",
                c = "date",
                u = /^(\d{4})[-/]?(\d{1,2})?[-/]?(\d{0,2})[^0-9]*(\d{1,2})?:?(\d{1,2})?:?(\d{1,2})?.?(\d+)?$/,
                d = /\[([^\]]+)]|Y{1,4}|M{1,4}|D{1,2}|d{1,4}|H{1,2}|h{1,2}|a|A|m{1,2}|s{1,2}|Z{1,2}|SSS/g,
                h = {
                    name: "en",
                    weekdays: "Sunday_Monday_Tuesday_Wednesday_Thursday_Friday_Saturday".split("_"),
                    months: "January_February_March_April_May_June_July_August_September_October_November_December".split("_")
                },
                p = function(e, t, r) {
                    var a = String(e);
                    return !a || a.length >= t ? e : "" + Array(t + 1 - a.length).join(r) + e
                },
                f = {
                    s: p,
                    z: function(e) {
                        var t = -e.utcOffset(),
                            r = Math.abs(t),
                            a = Math.floor(r / 60),
                            n = r % 60;
                        return (t <= 0 ? "+" : "-") + p(a, 2, "0") + ":" + p(n, 2, "0")
                    },
                    m: function e(t, r) {
                        if (t.date() < r.date()) return -e(r, t);
                        var a = 12 * (r.year() - t.year()) + (r.month() - t.month()),
                            n = t.clone().add(a, i),
                            o = r - n < 0,
                            s = t.clone().add(a + (o ? -1 : 1), i);
                        return +(-(a + (r - n) / (o ? n - s : s - n)) || 0)
                    },
                    a: function(e) {
                        return e < 0 ? Math.ceil(e) || 0 : Math.floor(e)
                    },
                    p: function(u) {
                        return {
                            M: i,
                            y: l,
                            w: o,
                            d: n,
                            D: c,
                            h: a,
                            m: r,
                            s: t,
                            ms: e,
                            Q: s
                        } [u] || String(u || "").toLowerCase().replace(/s$/, "")
                    },
                    u: function(e) {
                        return void 0 === e
                    }
                },
                m = "en",
                v = {};
            v[m] = h;
            var g = function(e) {
                    return e instanceof E
                },
                y = function(e, t, r) {
                    var a;
                    if (!e) return m;
                    if ("string" == typeof e) v[e] && (a = e), t && (v[e] = t, a = e);
                    else {
                        var n = e.name;
                        v[n] = e, a = n
                    }
                    return !r && a && (m = a), a || !r && m
                },
                b = function(e, t) {
                    if (g(e)) return e.clone();
                    var r = "object" == typeof t ? t : {};
                    return r.date = e, r.args = arguments, new E(r)
                },
                w = f;
            w.l = y, w.i = g, w.w = function(e, t) {
                return b(e, {
                    locale: t.$L,
                    utc: t.$u,
                    x: t.$x,
                    $offset: t.$offset
                })
            };
            var E = function() {
                    function h(e) {
                        this.$L = y(e.locale, null, !0), this.parse(e)
                    }
                    var p = h.prototype;
                    return p.parse = function(e) {
                        this.$d = function(e) {
                            var t = e.date,
                                r = e.utc;
                            if (null === t) return new Date(NaN);
                            if (w.u(t)) return new Date;
                            if (t instanceof Date) return new Date(t);
                            if ("string" == typeof t && !/Z$/i.test(t)) {
                                var a = t.match(u);
                                if (a) {
                                    var n = a[2] - 1 || 0,
                                        o = (a[7] || "0").substring(0, 3);
                                    return r ? new Date(Date.UTC(a[1], n, a[3] || 1, a[4] || 0, a[5] || 0, a[6] || 0, o)) : new Date(a[1], n, a[3] || 1, a[4] || 0, a[5] || 0, a[6] || 0, o)
                                }
                            }
                            return new Date(t)
                        }(e), this.$x = e.x || {}, this.init()
                    }, p.init = function() {
                        var e = this.$d;
                        this.$y = e.getFullYear(), this.$M = e.getMonth(), this.$D = e.getDate(), this.$W = e.getDay(), this.$H = e.getHours(), this.$m = e.getMinutes(), this.$s = e.getSeconds(), this.$ms = e.getMilliseconds()
                    }, p.$utils = function() {
                        return w
                    }, p.isValid = function() {
                        return !("Invalid Date" === this.$d.toString())
                    }, p.isSame = function(e, t) {
                        var r = b(e);
                        return this.startOf(t) <= r && r <= this.endOf(t)
                    }, p.isAfter = function(e, t) {
                        return b(e) < this.startOf(t)
                    }, p.isBefore = function(e, t) {
                        return this.endOf(t) < b(e)
                    }, p.$g = function(e, t, r) {
                        return w.u(e) ? this[t] : this.set(r, e)
                    }, p.unix = function() {
                        return Math.floor(this.valueOf() / 1e3)
                    }, p.valueOf = function() {
                        return this.$d.getTime()
                    }, p.startOf = function(e, s) {
                        var u = this,
                            d = !!w.u(s) || s,
                            h = w.p(e),
                            p = function(e, t) {
                                var r = w.w(u.$u ? Date.UTC(u.$y, t, e) : new Date(u.$y, t, e), u);
                                return d ? r : r.endOf(n)
                            },
                            f = function(e, t) {
                                return w.w(u.toDate()[e].apply(u.toDate("s"), (d ? [0, 0, 0, 0] : [23, 59, 59, 999]).slice(t)), u)
                            },
                            m = this.$W,
                            v = this.$M,
                            g = this.$D,
                            y = "set" + (this.$u ? "UTC" : "");
                        switch (h) {
                            case l:
                                return d ? p(1, 0) : p(31, 11);
                            case i:
                                return d ? p(1, v) : p(0, v + 1);
                            case o:
                                var b = this.$locale().weekStart || 0,
                                    E = (m < b ? m + 7 : m) - b;
                                return p(d ? g - E : g + (6 - E), v);
                            case n:
                            case c:
                                return f(y + "Hours", 0);
                            case a:
                                return f(y + "Minutes", 1);
                            case r:
                                return f(y + "Seconds", 2);
                            case t:
                                return f(y + "Milliseconds", 3);
                            default:
                                return this.clone()
                        }
                    }, p.endOf = function(e) {
                        return this.startOf(e, !1)
                    }, p.$set = function(o, s) {
                        var u, d = w.p(o),
                            h = "set" + (this.$u ? "UTC" : ""),
                            p = (u = {}, u[n] = h + "Date", u[c] = h + "Date", u[i] = h + "Month", u[l] = h + "FullYear", u[a] = h + "Hours", u[r] = h + "Minutes", u[t] = h + "Seconds", u[e] = h + "Milliseconds", u)[d],
                            f = d === n ? this.$D + (s - this.$W) : s;
                        if (d === i || d === l) {
                            var m = this.clone().set(c, 1);
                            m.$d[p](f), m.init(), this.$d = m.set(c, Math.min(this.$D, m.daysInMonth())).$d
                        } else p && this.$d[p](f);
                        return this.init(), this
                    }, p.set = function(e, t) {
                        return this.clone().$set(e, t)
                    }, p.get = function(e) {
                        return this[w.p(e)]()
                    }, p.add = function(e, s) {
                        var c, u = this;
                        e = Number(e);
                        var d = w.p(s),
                            h = function(t) {
                                var r = b(u);
                                return w.w(r.date(r.date() + Math.round(t * e)), u)
                            };
                        if (d === i) return this.set(i, this.$M + e);
                        if (d === l) return this.set(l, this.$y + e);
                        if (d === n) return h(1);
                        if (d === o) return h(7);
                        var p = (c = {}, c[r] = 6e4, c[a] = 36e5, c[t] = 1e3, c)[d] || 1,
                            f = this.$d.getTime() + e * p;
                        return w.w(f, this)
                    }, p.subtract = function(e, t) {
                        return this.add(-1 * e, t)
                    }, p.format = function(e) {
                        var t = this;
                        if (!this.isValid()) return "Invalid Date";
                        var r = e || "YYYY-MM-DDTHH:mm:ssZ",
                            a = w.z(this),
                            n = this.$locale(),
                            o = this.$H,
                            i = this.$m,
                            s = this.$M,
                            l = n.weekdays,
                            c = n.months,
                            u = function(e, a, n, o) {
                                return e && (e[a] || e(t, r)) || n[a].substr(0, o)
                            },
                            h = function(e) {
                                return w.s(o % 12 || 12, e, "0")
                            },
                            p = n.meridiem || function(e, t, r) {
                                var a = e < 12 ? "AM" : "PM";
                                return r ? a.toLowerCase() : a
                            },
                            f = {
                                YY: String(this.$y).slice(-2),
                                YYYY: this.$y,
                                M: s + 1,
                                MM: w.s(s + 1, 2, "0"),
                                MMM: u(n.monthsShort, s, c, 3),
                                MMMM: u(c, s),
                                D: this.$D,
                                DD: w.s(this.$D, 2, "0"),
                                d: String(this.$W),
                                dd: u(n.weekdaysMin, this.$W, l, 2),
                                ddd: u(n.weekdaysShort, this.$W, l, 3),
                                dddd: l[this.$W],
                                H: String(o),
                                HH: w.s(o, 2, "0"),
                                h: h(1),
                                hh: h(2),
                                a: p(o, i, !0),
                                A: p(o, i, !1),
                                m: String(i),
                                mm: w.s(i, 2, "0"),
                                s: String(this.$s),
                                ss: w.s(this.$s, 2, "0"),
                                SSS: w.s(this.$ms, 3, "0"),
                                Z: a
                            };
                        return r.replace(d, (function(e, t) {
                            return t || f[e] || a.replace(":", "")
                        }))
                    }, p.utcOffset = function() {
                        return 15 * -Math.round(this.$d.getTimezoneOffset() / 15)
                    }, p.diff = function(e, c, u) {
                        var d, h = w.p(c),
                            p = b(e),
                            f = 6e4 * (p.utcOffset() - this.utcOffset()),
                            m = this - p,
                            v = w.m(this, p);
                        return v = (d = {}, d[l] = v / 12, d[i] = v, d[s] = v / 3, d[o] = (m - f) / 6048e5, d[n] = (m - f) / 864e5, d[a] = m / 36e5, d[r] = m / 6e4, d[t] = m / 1e3, d)[h] || m, u ? v : w.a(v)
                    }, p.daysInMonth = function() {
                        return this.endOf(i).$D
                    }, p.$locale = function() {
                        return v[this.$L]
                    }, p.locale = function(e, t) {
                        if (!e) return this.$L;
                        var r = this.clone(),
                            a = y(e, t, !0);
                        return a && (r.$L = a), r
                    }, p.clone = function() {
                        return w.w(this.$d, this)
                    }, p.toDate = function() {
                        return new Date(this.valueOf())
                    }, p.toJSON = function() {
                        return this.isValid() ? this.toISOString() : null
                    }, p.toISOString = function() {
                        return this.$d.toISOString()
                    }, p.toString = function() {
                        return this.$d.toUTCString()
                    }, h
                }(),
                P = E.prototype;
            return b.prototype = P, [
                ["$ms", e],
                ["$s", t],
                ["$m", r],
                ["$H", a],
                ["$W", n],
                ["$M", i],
                ["$y", l],
                ["$D", c]
            ].forEach((function(e) {
                P[e[1]] = function(t) {
                    return this.$g(t, e[0], e[1])
                }
            })), b.extend = function(e, t) {
                return e.$i || (e(t, E, b), e.$i = !0), b
            }, b.locale = y, b.isDayjs = g, b.unix = function(e) {
                return b(1e3 * e)
            }, b.en = v[m], b.Ls = v, b.p = {}, b
        }()
    })),
    au = {
        setup(e) {
            const {
                img: t,
                className: r
            } = e;
            return {
                src: `/icon/${t}`,
                style: ["status", r]
            }
        },
        props: {
            className: String,
            img: String
        }
    };
au.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", {
        class: a.style
    }, [wa("img", {
        src: a.src
    }, null, 8, ["src"])], 2)
};
var nu = {
    data: () => ({
        errors: !1,
        edited: !1
    }),
    computed: {
        error() {
            return !(!this.errors || !this.errors[0]) && Hc(this.errors[0].keyword, this.errors[0].params)
        },
        isEdited() {
            return this.checkErrors(), this.edited || this.validator?.force_validate
        },
        style() {
            return !!this.isEdited && (this.errors ? "error" : "validated")
        }
    },
    methods: {
        checkErrors() {
            this.validator && (this.errors = this.validator.getErrors(this.name))
        },
        handleInputOnce() {
            this.edited = !0
        },
        handleInput(e) {
            this.validator && (this.validator.set(this.name, e.target.value), this.validator.validate(), this.checkErrors())
        },
        handleIconClick(e) {
            this.$emit("iconClick", e)
        }
    },
    props: {
        name: String,
        placeholder: {
            type: String,
            default: null
        },
        readonly: {
            type: String,
            default: null
        },
        disabled: {
            type: Boolean,
            default: null
        },
        icon: {
            type: String,
            value: null
        },
        validator: {
            type: Object,
            default: null
        }
    }
};
const ou = {
        key: 0,
        class: "error-text"
    },
    iu = wa("img", {
        src: Yc
    }, null, -1),
    su = {
        class: "message"
    };
nu.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", {
        class: ["message-wrapper", o.style]
    }, [o.isEdited && n.errors ? (ha(), fa("span", ou, [iu, Pa(u(o.error), 1)])) : _a("", !0), wa("div", su, [wa("textarea", {
        placeholder: r.placeholder,
        name: r.name,
        onInput: t[1] || (t[1] = (...e) => o.handleInput && o.handleInput(...e)),
        readonly: r.readonly,
        onInputOnce: t[2] || (t[2] = (...e) => o.handleInputOnce && o.handleInputOnce(...e)),
        disabled: r.disabled
    }, null, 40, ["placeholder", "name", "readonly", "disabled"])])], 2)
};
var lu = {
    props: {
        name: String,
        type: {
            type: String,
            default: "number"
        },
        value: String,
        showName: {
            type: Boolean,
            default: !0
        },
        showIcon: {
            type: Boolean,
            default: !0
        },
        options: {
            type: Object,
            default: null
        },
        title: {
            type: String,
            default: null
        },
        validator: {
            type: Object,
            default: null
        },
        disabled: {
            type: Boolean,
            default: !1
        }
    },
    mounted() {
        this.name && this.validator ? (this.active = this.transform(this.validator.data[this.name]), yr(this.validator.data, (e => {
            this.active = this.transform(e[this.name])
        }))) : this.active = this.value
    },
    computed: {
        list() {
            return Object.entries(this.options).map((([e, t]) => (t.id = this.transform(e), t))).sort(((e, t) => e.position - t.position))
        },
        error() {
            return !(!this.errors || !this.errors[0]) && Hc(this.errors[0].keyword, this.errors[0].params)
        },
        isEdited() {
            return this.checkErrors(), this.edited || this.name && this.validator?.force_validate
        }
    },
    data: () => ({
        errors: !1,
        edited: !1,
        active: null
    }),
    methods: {
        transform(e) {
            return "number" === this.type ? Number(e) : e
        },
        checkErrors() {
            this.name && this.validator && (this.errors = this.validator.getErrors(this.name))
        },
        handleClick(e, t) {
            this.disabled || (this.name && this.validator && (this.validator.set(this.name, t), this.validator.validate(), this.checkErrors()), this.$emit("change", e, t))
        }
    }
};
const cu = {
        class: "select-box"
    },
    uu = {
        class: "header"
    },
    du = {
        key: 0,
        class: "title"
    },
    hu = {
        key: 1,
        class: "error-text"
    },
    pu = wa("img", {
        src: Yc
    }, null, -1),
    fu = {
        class: "buttons-wrapper"
    },
    mu = {
        key: 1
    };
lu.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", cu, [wa("div", uu, [r.title ? (ha(), fa("div", du, u(r.title) + ":", 1)) : _a("", !0), o.isEdited && n.errors ? (ha(), fa("span", hu, [pu, Pa(u(o.error), 1)])) : _a("", !0)]), wa("div", fu, [(ha(!0), fa(ia, null, en(o.list, (e => (ha(), fa("div", {
        class: ["btn-select", {
            active: e.id === n.active,
            disabled: this.disabled
        }],
        key: e.id,
        onClick: t => o.handleClick(t, e.id)
    }, [e.icon && r.showIcon ? (ha(), fa("img", {
        key: 0,
        src: e.icon
    }, null, 8, ["src"])) : _a("", !0), r.showName ? (ha(), fa("span", mu, u(e.short || e.name || e.value), 1)) : _a("", !0)], 10, ["onClick"])))), 128))])])
};
var vu = {
    props: {
        feedback: Object
    },
    setup() {
        const {
            addNotify: e
        } = bc;
        return {
            addNotify: e
        }
    },
    data: () => ({
        ReportTypeEnum: eu,
        validator: new nc("feedback", "reportFeedback")
    }),
    computed: {
        icon() {
            return 1 === this.feedback.rate ? "arrow.svg" : "dash.svg"
        },
        color() {
            return 1 === this.feedback.rate ? "positive" : "neutral"
        }
    },
    methods: {
        getAvatarPath: gc,
        handleCloseClick() {
            this.$emit("close")
        },
        async handleSubmit() {
            this.validator.set("feedback_id", this.feedback.id);
            await this.validator.call() ? (this.addNotify({
                title: "Form accepted!",
                content: "Your form was submitted successfully!",
                type: "success"
            }), this.$emit("close")) : this.addNotify({
                title: "Fix the form",
                type: "error"
            })
        }
    },
    components: {
        ButtonGroup: lu,
        Message: nu,
        Input: qc,
        Status: au
    }
};
const gu = {
        id: "subpage-report_feedback",
        class: "subpage"
    },
    yu = {
        class: "scrollbar"
    },
    bu = {
        class: "page-heading"
    },
    wu = wa("img", {
        src: "/icon/close.svg"
    }, null, -1),
    Eu = wa("div", {
        class: "wrapper"
    }, [wa("div", {
        class: "heading"
    }, "Report feedback")], -1),
    Pu = {
        class: "content-wrapper"
    },
    ku = {
        class: "feedback-preview"
    },
    _u = {
        class: "left"
    },
    Su = {
        class: "avatar"
    },
    Cu = {
        class: "right"
    },
    Tu = {
        class: "comment"
    },
    xu = {
        class: "description"
    },
    Du = wa("div", {
        class: "title"
    }, "Description:", -1),
    Ou = {
        class: "proofs"
    },
    Ru = {
        class: "links"
    },
    Fu = wa("div", {
        class: "title"
    }, "Proof links (optional):", -1),
    $u = {
        class: "send-report"
    },
    Au = wa("span", {
        class: "text"
    }, "Send report", -1),
    Mu = wa("span", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/send.svg"
    })], -1);
vu.render = function(e, t, r, a, n, o) {
    const i = ta("Status"),
        s = ta("ButtonGroup"),
        l = ta("Message"),
        c = ta("Input");
    return ha(), fa("div", gu, [wa("div", yu, [wa("div", bu, [wa("div", {
        class: "close",
        onClick: t[1] || (t[1] = (...e) => o.handleCloseClick && o.handleCloseClick(...e))
    }, [wu]), Eu]), wa("div", Pu, [wa("div", ku, [wa("div", _u, [wa("div", Su, [wa("img", {
        src: o.getAvatarPath(r.feedback.avatar)
    }, null, 8, ["src"])]), wa(i, {
        className: o.color,
        img: o.icon
    }, null, 8, ["className", "img"])]), wa("div", Cu, [wa("div", {
        class: "nickname",
        innerHTML: r.feedback.username
    }, null, 8, ["innerHTML"]), wa("div", Tu, u(r.feedback.body), 1)])]), wa(s, {
        name: "type",
        title: "Report type",
        options: n.ReportTypeEnum,
        validator: n.validator
    }, null, 8, ["options", "validator"]), wa("div", xu, [Du, wa(l, {
        name: "body",
        validator: n.validator
    }, null, 8, ["validator"])]), wa("div", Ou, [wa("div", Ru, [Fu, wa(c, {
        name: "proof[0]",
        validator: n.validator
    }, null, 8, ["validator"])])]), wa("div", $u, [wa("button", {
        class: "btn btn-blue hvr-bounce-to-right",
        onClick: t[2] || (t[2] = (...e) => o.handleSubmit && o.handleSubmit(...e))
    }, [Au, Mu])])])])])
};
var Lu = {
    data: () => ({
        visible: !0,
        popup: !1
    }),
    setup() {
        const {
            logged: e
        } = mc, {
            addNotify: t
        } = bc;
        return {
            logged: e,
            PaymentMethodEnum: zc,
            TradePositionEnum: Jc,
            TradeTypeEnum: Qc,
            AppIdEnum: Xc,
            addNotify: t
        }
    },
    props: {
        link: String,
        data: Object
    },
    computed: {
        owner() {
            return this.logged && this.data.from_steam_id === mc.data.session.steam_id
        },
        style() {
            return `status_${this.data.status}`
        },
        profile_link() {
            return `/profile/${this.data[this.link]}`
        },
        icon() {
            return 1 === this.data.rate ? "arrow.svg" : "dash.svg"
        },
        color() {
            return 1 === this.data.rate ? "positive" : "neutral"
        },
        phrase() {
            const {
                data: e
            } = this, t = 5 === e.trade_type ? "worth" : "for", r = e.amount <= 0 ? "" : `${t} <span class="price-green">$${((e,t=" ")=>e.toString().replace(/\B(?=(\d{3})+(?!\d))/g,t))(e.amount)}</span>`, a = null === e.app_id ? "" : `${Xc[e.app_id]&&Xc[e.app_id].short}`;
            return `<strong>Transaction:</strong> ${Qc[e.trade_type].phrase} ${a} ${Qc[e.trade_type].trade_type}\n             ${r} by <span class="price-green">${zc[e.payment_method].name}</span>`
        }
    },
    methods: {
        getDay: e => ru(e).format("YYYY-MM-DD HH:mm"),
        getAvatarPath: gc,
        show_popup() {
            mc.data.session.email ? this.popup = !0 : this.$router.push("/email")
        },
        async handleDelete(e) {
            try {
                await uc("feedback", "delete", {
                    id: e
                }), this.addNotify({
                    title: "Record has been deleted",
                    type: "success"
                }), this.visible = !1
            } catch (e) {
                this.addNotify({
                    title: "Cannot delete this record",
                    type: "error"
                })
            }
        }
    },
    components: {
        Status: au,
        ReportPopup: vu
    }
};
const Nu = {
        class: "recommendations"
    },
    Iu = {
        key: 0,
        class: "reviews-wrapper"
    },
    ju = wa("div", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/good_review.svg"
    })], -1),
    Uu = {
        class: "amount"
    },
    Hu = wa("div", {
        class: "hover"
    }, "View Profile", -1),
    qu = {
        key: 0,
        class: "added-by-staff"
    },
    Yu = wa("span", {
        class: "staff-title"
    }, "- modified by staff", -1),
    Bu = {
        class: "icons"
    },
    Wu = {
        key: 0,
        src: "/icon/verified.svg"
    },
    Vu = {
        key: 0,
        class: "flag"
    },
    zu = {
        class: "comment-number"
    },
    Xu = {
        class: "container"
    };
Lu.render = function(e, t, r, a, n, o) {
    const i = ta("router-link"),
        s = ta("Status"),
        l = ta("ReportPopup");
    return n.visible ? (ha(), fa("div", {
        key: 0,
        class: ["el", o.style]
    }, [wa("div", Nu, [wa(i, {
        to: o.profile_link,
        class: "nickname",
        innerHTML: r.data.username
    }, null, 8, ["to", "innerHTML"]), r.data.feedback.positive > 0 ? (ha(), fa("div", Iu, [ju, wa("div", Uu, u(r.data.feedback.positive), 1)])) : _a("", !0)]), wa(i, {
        class: "avatar",
        to: o.profile_link
    }, {
        default: Vt((() => [Hu, wa("img", {
            src: o.getAvatarPath(r.data.avatar),
            class: o.color
        }, null, 10, ["src"])])),
        _: 1
    }, 8, ["to"]), wa(s, {
        className: o.color,
        img: o.icon
    }, null, 8, ["className", "img"]), wa("div", {
        class: ["content", {
            owner: o.owner
        }]
    }, [wa("div", {
        class: "transaction-title",
        innerHTML: o.phrase
    }, null, 8, ["innerHTML"]), wa("p", null, u(r.data.body), 1), r.data.admin_comment ? (ha(), fa("p", qu, [Pa(u(r.data.admin_comment) + " ", 1), Yu])) : _a("", !0)], 2), wa("div", Bu, [2 === r.data.status ? (ha(), fa("img", Wu)) : _a("", !0), r.data.payment_method && a.PaymentMethodEnum[r.data.payment_method] ? (ha(), fa("img", {
        key: 1,
        src: a.PaymentMethodEnum[r.data.payment_method].icon
    }, null, 8, ["src"])) : _a("", !0), r.data.trade_position && a.TradePositionEnum[r.data.trade_position] ? (ha(), fa("img", {
        key: 2,
        src: a.TradePositionEnum[r.data.trade_position].icon
    }, null, 8, ["src"])) : _a("", !0)]), a.logged ? (ha(), fa("div", Vu, [o.owner ? (ha(), fa("div", {
        key: 0,
        class: "btn btn-red",
        onClick: t[1] || (t[1] = () => o.handleDelete(r.data.id))
    }, "Delete")) : _a("", !0), wa("div", zu, u(o.getDay(r.data.created_at)) + " | #" + u(r.data.id), 1), wa("img", {
        src: "/icon/flag.svg",
        onClick: t[2] || (t[2] = (...e) => o.show_popup && o.show_popup(...e))
    })])) : _a("", !0), a.logged && n.popup ? (ha(), fa(ea, {
        key: 1,
        to: "#popup"
    }, [wa("div", Xu, [wa(l, {
        feedback: r.data,
        onClose: t[3] || (t[3] = e => n.popup = !1)
    }, null, 8, ["feedback"])])])) : _a("", !0)], 2)) : _a("", !0)
};
var Qu = {
    props: {
        show: Boolean
    }
};
const Gu = {
        key: 0,
        class: "subloader"
    },
    Ku = wa("img", {
        src: "/icon/loader.svg",
        class: "animation"
    }, null, -1);
Qu.render = function(e, t, r, a, n, o) {
    return ha(), fa(Pn, {
        name: "fade-fast"
    }, {
        default: Vt((() => [r.show ? (ha(), fa("div", Gu, [Ku])) : _a("", !0)])),
        _: 1
    })
};
const Ju = {
    none: {
        name: "",
        icon: "/icon/cross.svg",
        where: void 0
    },
    balance: {
        name: "",
        icon: "/icon/social/buff.svg",
        where: {
            trade_type: [3, 4]
        }
    },
    crypto: {
        name: "",
        icon: "/icon/payment/btc.svg",
        where: {
            payment_method: [1, 2, 3, 4]
        }
    },
    cash: {
        name: "",
        icon: "/icon/payment/cash.svg",
        where: {
            payment_method: [5, 6, 7, 8, 9]
        }
    }
};
var Zu = {
    props: {
        steam_id: String
    },
    data: () => ({
        FilterEnum: Ju,
        filter: "none",
        where: void 0,
        loaded: !1,
        order: "id,DESC",
        list: null
    }),
    watch: {
        steam_id() {
            this.handleSearch()
        }
    },
    mounted() {
        this.handleSearch()
    },
    computed: {
        view() {
            return this.steam_id ? "creator" : "receiver"
        },
        link() {
            return this.steam_id ? "from_steam_id" : "to_steam_id"
        }
    },
    methods: {
        async handleSearch() {
            this.loaded = !1;
            const {
                view: e,
                where: t
            } = this, [r, a] = this.order.split(","), n = {
                filter: {
                    to_steam_id: this.steam_id
                },
                view: e,
                where: t,
                order_by: [{
                    field: r,
                    order: a
                }]
            }, {
                data: o
            } = await uc("feedback", "list", n);
            this.list = o, this.loaded = !0
        },
        handleFilter(e, t) {
            this.filter = t, this.where = void 0, this.FilterEnum[t] && (this.where = this.FilterEnum[t].where), this.handleSearch()
        }
    },
    components: {
        ButtonGroup: lu,
        SubLoader: Qu,
        Record: Lu
    }
};
const ed = {
        key: 0,
        class: "list history"
    },
    td = {
        class: "header"
    },
    rd = wa("h2", null, "Transaction history:", -1),
    ad = {
        class: "filter"
    },
    nd = {
        class: "sort"
    },
    od = wa("span", null, "Sort by:", -1),
    id = wa("option", {
        value: "id,ASC",
        selected: ""
    }, "date ascending", -1),
    sd = wa("option", {
        value: "id,DESC"
    }, "date descending", -1),
    ld = wa("option", {
        value: "amount,ASC"
    }, "price ascending", -1),
    cd = wa("option", {
        value: "amount,DESC"
    }, "price descending", -1),
    ud = {
        key: 0,
        class: "record-content"
    },
    dd = {
        key: 1,
        class: "no-records"
    },
    hd = wa("div", {
        class: "wrapper"
    }, [wa("img", {
        class: "sad_face",
        src: "/icon/sad_face.svg"
    }), wa("h1", null, "No records found")], -1);
Zu.render = function(e, t, r, a, n, o) {
    const i = ta("SubLoader"),
        s = ta("ButtonGroup"),
        l = ta("Record");
    return ha(), fa(ia, null, [wa(i, {
        show: !n.loaded
    }, null, 8, ["show"]), wa(Pn, {
        name: "fade-fast"
    }, {
        default: Vt((() => [n.loaded ? (ha(), fa("div", ed, [wa("div", td, [rd, wa("div", ad, [wa(s, {
            type: "string",
            value: n.filter,
            options: n.FilterEnum,
            title: "Filter",
            onChange: o.handleFilter
        }, null, 8, ["value", "options", "onChange"])]), wa("div", nd, [od, Ir(wa("select", {
            "onUpdate:modelValue": t[1] || (t[1] = e => n.order = e),
            onChange: t[2] || (t[2] = (...e) => o.handleSearch && o.handleSearch(...e))
        }, [id, sd, ld, cd], 544), [
            [Ln, n.order]
        ])])]), n.list.length > 0 ? (ha(), fa("div", ud, [(ha(!0), fa(ia, null, en(n.list, ((e, t) => (ha(), fa(l, {
            key: t,
            data: e,
            link: o.link
        }, null, 8, ["data", "link"])))), 128))])) : (ha(), fa("div", dd, [hd]))])) : _a("", !0)])),
        _: 1
    })], 64)
};
const pd = Ze(null),
    fd = Ze(null),
    md = Ze(null);
var vd;
vd = () => {
    uc("feedback", "stats").then((e => {
        pd.value = e.users, fd.value = e.feedbacks, md.value = e.bans
    }))
}, yr(sc, (async (e, t) => {
    e && !t && vd()
}));
var gd = {
    setup: () => ({
        users: pd,
        feedbacks: fd,
        bans: md
    }),
    components: {
        Status: au
    }
};
const yd = {
        class: "statistics"
    },
    bd = {
        class: "statistics__wrapper"
    },
    wd = {
        class: "stats-box positive_feedbacks"
    },
    Ed = {
        class: "stats"
    },
    Pd = {
        class: "number"
    },
    kd = wa("div", {
        class: "title"
    }, "POSITIVE FEEDBACKS", -1),
    _d = {
        class: "stats-box banned_users"
    },
    Sd = {
        class: "stats"
    },
    Cd = {
        class: "number"
    },
    Td = wa("div", {
        class: "title"
    }, "BANNED USERS", -1),
    xd = {
        class: "stats-box users_registered"
    },
    Dd = {
        class: "stats"
    },
    Od = {
        class: "number"
    },
    Rd = wa("div", {
        class: "title"
    }, "USERS REGISTERED", -1);
gd.render = function(e, t, r, a, n, o) {
    const i = ta("Status");
    return ha(), fa("div", yd, [wa("div", bd, [wa("div", wd, [wa(i, {
        className: "green",
        img: "arrow.svg"
    }), wa("div", Ed, [wa("div", Pd, u(a.feedbacks), 1), kd])]), wa("div", _d, [wa(i, {
        className: "red",
        img: "cross.svg"
    }), wa("div", Sd, [wa("div", Cd, u(a.bans), 1), Td])]), wa("div", xd, [wa(i, {
        className: "blue",
        img: "user.svg"
    }), wa("div", Dd, [wa("div", Od, u(a.users), 1), Rd])])])])
};
const Fd = {
        class: "advertisement"
    },
    $d = wa("div", {
        class: "content"
    }, [wa("div", {
        class: "banner-wrapper"
    }, [wa("a", {
        href: "/",
        target: "_blank"
    }, [wa("img", {
        class: "banner",
        src: "/partners/bs-3.png"
    })])])], -1);
const Ad = {
    render: function(e, t) {
        return ha(), fa("div", Fd, [$d])
    }
};
var Md = {
    props: {
        list: Object
    },
    computed: {
        routes() {
            return this.$root.routes
        }
    },
    components: {
        FooterAd: Ad,
        Icon: jc,
        FooterStats: gd
    }
};
const Ld = {
        class: "nav-wrapper"
    },
    Nd = wa("div", {
        class: "additional-info"
    }, [wa("img", {
        src: "/logo.svg"
    }), wa("div", {
        class: "text"
    }, [wa("p", null, "Website to keep track of your cash trades, find trustworthy"), wa("p", null, "users to do transactions with and avoid risky trades"), wa("p", null, "by easily checking someone's transaction history."), wa("p", null, "Founded in 2020.")])], -1),
    Id = {
        class: "nav"
    },
    jd = wa("div", {
        class: "title"
    }, "Menu CSGOREP", -1),
    Ud = {
        classs: "buttons"
    },
    Hd = {
        class: "nav-btn"
    },
    qd = wa("img", {
        src: "/icon/li.svg"
    }, null, -1),
    Yd = wa("div", {
        class: "bg"
    }, [wa("img", {
        src: "/weapons.png"
    })], -1),
    Bd = wa("div", {
        class: "left"
    }, [wa("div", {
        class: "statement"
    }, [wa("span", {
        class: "version"
    }, "v1.12"), Pa("CSGOrep 2020. Powered by Steam. Not affiliated with Valve Corp.")])], -1),
    Wd = {
        class: "right"
    },
    Vd = {
        href: "https://twitter.com/CSGORepCom",
        target: "_blank",
        class: "twitter"
    },
    zd = Pa("@CSGORepCom");
Md.render = function(e, t, r, a, n, o) {
    const i = ta("FooterAd"),
        s = ta("FooterStats"),
        l = ta("router-link"),
        c = ta("Icon");
    return ha(), fa(ia, null, [wa(i), wa(s), wa("div", Ld, [Nd, wa("div", Id, [jd, wa("div", Ud, [(ha(!0), fa(ia, null, en(o.routes, (e => (ha(), fa(l, {
        to: e.to,
        key: e.path
    }, {
        default: Vt((() => [wa("div", Hd, [qd, Pa(" " + u(e.text), 1)])])),
        _: 2
    }, 1032, ["to"])))), 128))])]), Yd]), wa("footer", null, [Bd, wa("div", Wd, [wa("a", Vd, [wa(c, {
        className: "social-icon",
        img: "social/twitter_footer.svg"
    }), zd])])])], 64)
};
var Xd = {
    components: {
        Icon: jc,
        Input: qc,
        TransactionHistory: Zu,
        Footer: Md
    },
    data: () => ({
        validator: new nc("feedback", "searchUser")
    }),
    methods: {
        handleSearch() {
            this.validator.force(), this.validator.validate() && this.$router.push(`/profile/${this.validator.data.steam_id}`)
        },
        handlePaste(e) {
            e.preventDefault();
            const t = e.clipboardData.getData("Text").replace(/\D/gi, "");
            return t.length > 0 && (this.validator.set("steam_id", t), this.validator.validate()), !1
        }
    }
};
const Qd = {
        id: "subpage-browse",
        class: "subpage"
    },
    Gd = {
        class: "search"
    },
    Kd = wa("div", {
        class: "heading"
    }, "Search user", -1),
    Jd = {
        class: "description"
    },
    Zd = wa("span", null, "Enter SteamID64 here", -1);
Xd.render = function(e, t, r, a, n, o) {
    const i = ta("Input"),
        s = ta("Icon"),
        l = ta("TransactionHistory"),
        c = ta("Footer");
    return ha(), fa("div", Qd, [wa("div", Gd, [Kd, wa(i, {
        icon: "/icon/magnifier.svg",
        name: "steam_id",
        placeholder: "SteamID64",
        validator: n.validator,
        onPaste: o.handlePaste,
        onKeyup: Yn(o.handleSearch, ["enter"]),
        onIconClick: o.handleSearch
    }, null, 8, ["validator", "onPaste", "onKeyup", "onIconClick"]), wa("div", Jd, [Zd, wa(s, {
        className: "icon-arrow",
        img: "curve_arrow.svg"
    })])]), wa(l), wa(c)])
};
var eh = {
    setup(e) {
        const {
            folderName: t,
            img: r,
            className: a
        } = e;
        return {
            src: `/icon/${t}/${r}`,
            style: ["social", a]
        }
    },
    props: {
        folderName: {
            type: String,
            default: "social"
        },
        img: String,
        className: String
    }
};
eh.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", {
        class: a.style
    }, [wa("img", {
        src: a.src
    }, null, 8, ["src"])], 2)
};
var th = {
    props: {
        profile: Object,
        ban: Object
    },
    setup() {
        const {
            addNotify: e
        } = bc;
        return {
            addNotify: e
        }
    },
    computed: {
        my_profile() {
            return mc.logged.value && this.profile.steam_id !== mc.data.session?.steam_id
        },
        inner() {
            return this.profile && this.profile.feedback && this.profile.feedback.positive > this.profile.feedback.neutral ? "positive" : "neutral"
        }
    },
    methods: {
        getAvatarPath: gc,
        getProfileUrl: yc,
        handleCopySteamLink() {
            const e = document.getElementsByTagName("input")[0];
            e.select(), document.execCommand("copy"), e.blur(), this.addNotify({
                title: "Link copied",
                type: "info"
            })
        },
        handleCopyRepLink() {
            const e = document.getElementsByTagName("input")[1];
            e.select(), document.execCommand("copy"), e.blur(), this.addNotify({
                title: "Link copied",
                type: "info"
            })
        }
    },
    components: {
        Icon: jc,
        Social: eh
    }
};
const rh = {
        key: 0,
        class: "profile-header"
    },
    ah = {
        class: "stats-wrapper"
    },
    nh = {
        key: 0,
        class: "rating"
    },
    oh = {
        class: "circle green"
    },
    ih = {
        class: "circle yellow"
    },
    sh = {
        class: "avatar-placehold"
    },
    lh = {
        class: "info-wrapper"
    },
    ch = {
        class: "profile-link"
    },
    uh = wa("img", {
        src: "/icon/copy.svg"
    }, null, -1),
    dh = {
        class: "profile-link"
    },
    hh = wa("img", {
        src: "/icon/copy.svg"
    }, null, -1),
    ph = {
        class: "info"
    },
    fh = {
        key: 0,
        class: "el"
    },
    mh = wa("img", {
        src: "/icon/add_user.svg"
    }, null, -1),
    vh = wa("strong", null, "Joined steam:", -1),
    gh = {
        key: 1,
        class: "el"
    },
    yh = wa("img", {
        src: "/icon/handshake.svg"
    }, null, -1),
    bh = wa("strong", null, "Done deals:", -1),
    wh = {
        class: "linked-accounts"
    },
    Eh = wa("span", null, "Linked accounts:", -1),
    Ph = {
        key: 1,
        class: "add-feedback"
    },
    kh = wa("div", {
        class: "text"
    }, "Add feedback", -1),
    _h = wa("div", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/send.svg"
    })], -1),
    Sh = {
        key: 2,
        class: "summary"
    },
    Ch = {
        class: "summary-wrapper"
    },
    Th = {
        class: "el"
    },
    xh = wa("strong", null, "Cash deals:", -1),
    Dh = {
        class: "el"
    },
    Oh = wa("strong", null, "Crypto deals:", -1),
    Rh = {
        class: "el"
    },
    Fh = wa("strong", null, "Balance deals:", -1);
th.render = function(e, t, r, a, n, o) {
    const i = ta("Icon"),
        s = ta("Social"),
        l = ta("router-link");
    return ha(), fa(ia, null, [r.profile ? (ha(), fa("div", rh, [wa("div", {
        class: ["header", {
            ban: r.ban
        }]
    }, [wa("div", ah, [r.profile.feedback ? (ha(), fa("div", nh, [wa("div", oh, [wa(i, {
        img: "arrow.svg"
    }), wa("span", null, u(r.profile.feedback.positive), 1)]), wa("div", ih, [wa(i, {
        img: "dash.svg"
    }), wa("span", null, u(r.profile.feedback.neutral), 1)])])) : _a("", !0), wa("div", sh, [wa("div", {
        class: ["inner", o.inner]
    }, [wa("img", {
        src: o.getAvatarPath(r.profile.avatar),
        class: "avatar"
    }, null, 8, ["src"])], 2)])]), wa("div", lh, [wa("h1", {
        class: "nickname",
        innerHTML: r.profile.username
    }, null, 8, ["innerHTML"]), wa("div", ch, [wa("input", {
        value: o.getProfileUrl(r.profile.steam_id),
        readonly: "true"
    }, null, 8, ["value"]), wa("button", {
        onClick: t[1] || (t[1] = (...e) => o.handleCopySteamLink && o.handleCopySteamLink(...e))
    }, [uh])]), wa("div", dh, [wa("input", {
        value: "https://steam-rep.com/profile/" + r.profile.steam_id,
        readonly: "true"
    }, null, 8, ["value"]), wa("button", {
        onClick: t[2] || (t[2] = (...e) => o.handleCopyRepLink && o.handleCopyRepLink(...e))
    }, [hh])]), wa("div", ph, [r.profile.steam_created_at ? (ha(), fa("div", fh, [mh, vh, wa("span", null, u(r.profile.steam_created_at), 1)])) : _a("", !0), r.profile.feedback ? (ha(), fa("div", gh, [yh, bh, wa("span", null, u(r.profile.feedback.neutral + r.profile.feedback.positive), 1)])) : _a("", !0)]), wa("div", wh, [Eh, wa("a", {
        href: o.getProfileUrl(r.profile.steam_id),
        rel: "nofollow noopener",
        target: "_blank"
    }, [wa(s, {
        className: "steam",
        img: "steam.svg"
    })], 8, ["href"]), wa("a", {
        href: "http://steamrep.com/search?q=" + r.profile.steam_id,
        rel: "nofollow noopener",
        target: "_blank"
    }, [wa(s, {
        className: "no-filter",
        img: "steamrep.svg"
    })], 8, ["href"]), r.profile.link_youtube ? (ha(), fa("a", {
        key: 0,
        href: r.profile.link_youtube,
        rel: "nofollow noopener",
        target: "_blank"
    }, [wa(s, {
        className: "yt",
        img: "youtube.svg"
    })], 8, ["href"])) : _a("", !0), r.profile.link_buff ? (ha(), fa("a", {
        key: 1,
        href: r.profile.link_buff,
        rel: "nofollow noopener",
        target: "_blank"
    }, [wa(s, {
        className: "buff",
        img: "buff.svg"
    })], 8, ["href"])) : _a("", !0), r.profile.link_bitskins ? (ha(), fa("a", {
        key: 2,
        href: "https://bitskins.com/inventory?uid=" + r.profile.steam_id,
        rel: "nofollow noopener",
        target: "_blank"
    }, [wa(s, {
        className: "bitskins",
        img: "bitskins.svg"
    })], 8, ["href"])) : _a("", !0)])])], 2)])) : _a("", !0), o.my_profile ? (ha(), fa("div", Ph, [wa(l, {
        to: `/feedback/${r.profile.steam_id}`,
        class: "btn btn-blue hvr-bounce-to-right"
    }, {
        default: Vt((() => [kh, _h])),
        _: 1
    }, 8, ["to"])])) : _a("", !0), r.profile ? (ha(), fa("div", Sh, [wa("div", Ch, [wa("div", Th, [wa(s, {
        className: "paypal",
        folderName: "payment",
        img: "usdt.svg"
    }), xh, wa("span", null, u(r.profile.feedback.cash), 1)]), wa("div", Dh, [wa(s, {
        className: "bitcoin",
        img: "btc.svg",
        folderName: "payment"
    }), Oh, wa("span", null, u(r.profile.feedback.crypto), 1)]), wa("div", Rh, [wa(s, {
        folderName: "social",
        img: "buff.svg",
        className: "buff"
    }), Fh, wa("span", null, u(r.profile.feedback.balance), 1)])])])) : _a("", !0)], 64)
};
var $h = {
    data: () => ({
        loaded: !1,
        not_found: !1,
        ban: null,
        profile: null
    }),
    setup: () => ({
        BanReasonEnum: tu
    }),
    async mounted() {
        await this.load(this.$route.params.steam_id)
    },
    watch: {
        "$route.params.steam_id": function(e) {
            this.load(e)
        }
    },
    methods: {
        async load(e) {
            e || (e = mc.data.session.steam_id);
            const {
                profile: t,
                ban: r
            } = await uc("feedback", "getProfile", {
                steam_id: e
            });
            t || (this.not_found = !0), this.profile = t || {
                steam_id: e
            }, this.ban = r, this.loaded = !0
        }
    },
    components: {
        ProfileHeader: th,
        TransactionHistory: Zu,
        Footer: Md
    }
};
const Ah = {
        key: 0,
        id: "subpage-profile",
        class: "subpage"
    },
    Mh = {
        key: 0,
        class: "ban"
    },
    Lh = {
        class: "ban-warning"
    },
    Nh = wa("div", {
        class: "title"
    }, [wa("img", {
        src: "/icon/warning.svg",
        class: "warning"
    }), Pa(" BANNED")], -1),
    Ih = {
        class: "text"
    },
    jh = {
        class: "steam_id"
    },
    Uh = {
        key: 1,
        class: "not_found"
    },
    Hh = {
        key: 2
    };
$h.render = function(e, t, r, a, n, o) {
    const i = ta("ProfileHeader"),
        s = ta("TransactionHistory"),
        l = ta("Footer");
    return n.loaded ? (ha(), fa("div", Ah, [n.ban ? (ha(), fa("div", Mh, [wa("div", Lh, [Nh, wa("div", Ih, "this user is banned for " + u(a.BanReasonEnum[n.ban.reason].reason), 1)]), wa(i, {
        profile: n.profile,
        ban: n.ban
    }, null, 8, ["profile", "ban"]), wa("div", jh, u(e.steam_id), 1)])) : n.not_found ? (ha(), fa("div", Uh, " Profile not found :( ")) : (ha(), fa("div", Hh, [wa(i, {
        profile: n.profile
    }, null, 8, ["profile"]), wa(s, {
        steam_id: n.profile.steam_id
    }, null, 8, ["steam_id"]), wa(l)]))])) : _a("", !0)
};
var qh = {
    props: {
        name: String,
        options: {
            type: Array,
            default: []
        },
        readonly: {
            type: String,
            default: null
        },
        disabled: {
            type: Boolean,
            default: null
        },
        validator: {
            type: Object,
            default: null
        }
    },
    data: () => ({
        errors: !1,
        edited: !1
    }),
    computed: {
        value() {
            return this.validator?.data[this.name]
        },
        error() {
            return !(!this.errors || !this.errors[0]) && Hc(this.errors[0].keyword, this.errors[0].params)
        },
        isEdited() {
            return this.checkErrors(), this.edited || this.validator?.force_validate
        },
        style() {
            return !!this.isEdited && (this.errors ? "error" : "validated")
        }
    },
    methods: {
        checkErrors() {
            this.validator && (this.errors = this.validator.getErrors(this.name))
        },
        handleInputOnce() {
            this.edited = !0
        },
        parseValue(e) {
            return "number" === this.type ? "" === e ? null : Number(e) : e
        },
        handleInput(e) {
            this.validator && (this.validator.set(this.name, this.parseValue(e.target.value)), this.validator.validate(), this.checkErrors())
        },
        handleIconClick(e) {
            this.$emit("iconClick", e)
        }
    }
};
const Yh = {
        key: 0,
        class: "error-text"
    },
    Bh = wa("img", {
        src: Yc
    }, null, -1),
    Wh = {
        class: "input"
    };
qh.render = function(e, t, r, a, n, o) {
    return ha(), fa("div", {
        class: ["input-wrapper", o.style]
    }, [o.isEdited && n.errors ? (ha(), fa("span", Yh, [Bh, Pa(u(o.error), 1)])) : _a("", !0), wa("div", Wh, [wa("select", {
        name: r.name,
        onInput: t[1] || (t[1] = (...e) => o.handleInput && o.handleInput(...e)),
        onInputOnce: t[2] || (t[2] = (...e) => o.handleInputOnce && o.handleInputOnce(...e)),
        readonly: r.readonly,
        disabled: r.disabled,
        onBlur: t[3] || (t[3] = t => e.$emit("blur"))
    }, [(ha(!0), fa(ia, null, en(r.options, (e => (ha(), fa("option", {
        value: e,
        key: e,
        selected: e === o.value
    }, u(e), 9, ["value", "selected"])))), 128))], 40, ["name", "readonly", "disabled"])])], 2)
};
var Vh = {
    setup() {
        const {
            addNotify: e
        } = bc;
        return {
            addNotify: e
        }
    },
    data: () => ({
        options: ["Ban appeal", "General", "Suggestion", "Business", "Other"],
        submitted: !1,
        validator: new nc("contact", "send")
    }),
    methods: {
        async handleSubmit() {
            try {
                await this.validator.call() ? (this.addNotify({
                    title: "Form accepted!",
                    content: "Your form was submitted successfully!",
                    type: "success"
                }), this.submitted = !0) : this.addNotify({
                    title: "Fix the form",
                    type: "error"
                })
            } catch (e) {
                this.addNotify({
                    title: "Fix the form",
                    content: e.error,
                    type: "error"
                })
            }
        }
    },
    components: {
        Input: qc,
        Message: nu,
        Footer: Md,
        Select: qh
    }
};
const zh = {
        id: "subpage-contact",
        class: "subpage"
    },
    Xh = wa("div", {
        class: "page-heading"
    }, "CONTACT", -1),
    Qh = {
        class: "contact"
    },
    Gh = {
        class: "reason"
    },
    Kh = wa("div", {
        class: "title"
    }, "Reason", -1),
    Jh = {
        class: "email"
    },
    Zh = wa("div", {
        class: "title"
    }, "E-mail", -1),
    ep = {
        class: "title"
    },
    tp = wa("div", {
        class: "title"
    }, "Title", -1),
    rp = {
        class: "message"
    },
    ap = wa("div", {
        class: "title"
    }, "Message:", -1),
    np = {
        class: "send-message"
    },
    op = wa("span", {
        class: "text"
    }, "Send message", -1),
    ip = wa("span", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/send.svg"
    })], -1),
    sp = {
        key: 1,
        class: "submitted"
    },
    lp = wa("div", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/successful.svg"
    }), wa("div", {
        class: "title"
    }, "Thank you!")], -1),
    cp = wa("div", {
        class: "content"
    }, " The form was submitted successfully. ", -1);
Vh.render = function(e, t, r, a, n, o) {
    const i = ta("Select"),
        s = ta("Input"),
        l = ta("Message"),
        c = ta("Footer");
    return ha(), fa("div", zh, [Xh, n.submitted ? (ha(), fa("div", sp, [lp, cp])) : (ha(), fa("div", {
        key: 0,
        class: "content-wrapper",
        onKeyup: t[2] || (t[2] = Yn(((...e) => o.handleSubmit && o.handleSubmit(...e)), ["enter"]))
    }, [wa("div", Qh, [wa("div", Gh, [Kh, wa(i, {
        name: "reason",
        options: n.options,
        validator: n.validator
    }, null, 8, ["options", "validator"])]), wa("div", Jh, [Zh, wa(s, {
        placeholder: "E-mail",
        name: "email",
        validator: n.validator
    }, null, 8, ["validator"])]), wa("div", ep, [tp, wa(s, {
        placeholder: "Title",
        name: "title",
        validator: n.validator
    }, null, 8, ["validator"])]), wa("div", rp, [ap, wa(l, {
        placeholder: "Message",
        name: "body",
        validator: n.validator
    }, null, 8, ["validator"])])]), wa("div", np, [wa("button", {
        class: ["btn btn-blue hvr-bounce-to-right", {
            disabled: !n.validator.valid
        }],
        onClick: t[1] || (t[1] = (...e) => o.handleSubmit && o.handleSubmit(...e))
    }, [op, ip], 2)])], 32)), wa(c)])
};
var up = {
    setup() {
        const {
            addNotify: e
        } = bc;
        return {
            addNotify: e
        }
    },
    data: () => ({
        UserTradeStatusEnum: Zc,
        profile: null,
        validator: new nc("user", "email")
    }),
    methods: {
        getBitskinsUrl: e => `https://bitskins.com/inventory?uid=${e}&app_id=730`,
        getProfileUrl: yc,
        async handleBitskinsLink() {
            await uc("user", "bitskins", {
                action: 1
            }), this.addNotify({
                title: "Bitskins account linked!",
                type: "success"
            }), this.profile.link_bitskins = 1
        },
        async handleBitskinsUnlink() {
            await uc("user", "bitskins", {
                action: 0
            }), this.addNotify({
                title: "Bitskins account unlinked!",
                type: "warning"
            }), this.profile.link_bitskins = 0
        },
        async handleSubmit() {
            await this.validator.call() ? this.addNotify({
                title: "Profile updated!",
                content: "Your profile has been updated!",
                type: "success"
            }) : this.addNotify({
                title: "Fix the form",
                type: "error"
            })
        }
    },
    async mounted() {
        const {
            steam_id: e
        } = mc.data.session, {
            profile: t
        } = await uc("feedback", "getProfile", {
            steam_id: e
        });
        this.profile = t, this.validator.setData(cs(t))
    },
    components: {
        ProfileHeader: th,
        Social: eh,
        Input: qc,
        Footer: Md
    }
};
const dp = {
        key: 0,
        id: "subpage-settings",
        class: "subpage"
    },
    hp = {
        class: "content-wrapper"
    },
    pp = {
        class: "linked-accounts"
    },
    fp = wa("div", {
        class: "title"
    }, "Your email address:", -1),
    mp = {
        class: "wrapper"
    },
    vp = {
        class: "linked"
    },
    gp = wa("div", {
        class: "text"
    }, "Update", -1),
    yp = wa("div", {
        class: "send-message"
    }, null, -1),
    bp = {
        class: "linked-accounts"
    },
    wp = wa("div", {
        class: "title"
    }, "Linked accounts:", -1),
    Ep = {
        class: "wrapper"
    },
    Pp = {
        class: "linked bs"
    },
    kp = {
        key: 0
    },
    _p = wa("div", {
        class: "text"
    }, "Unlink", -1),
    Sp = wa("div", {
        class: "text"
    }, "Link", -1);
up.render = function(e, t, r, a, n, o) {
    const i = ta("ProfileHeader"),
        s = ta("Social"),
        l = ta("Input"),
        c = ta("Footer");
    return n.profile ? (ha(), fa("div", dp, [wa(i, {
        profile: n.profile
    }, null, 8, ["profile"]), wa("div", hp, [wa("div", pp, [fp, wa("div", mp, [wa("div", vp, [wa(s, {
        folderName: "",
        img: "email.svg",
        className: ""
    }), wa(l, {
        placeholder: "email...",
        name: "email",
        validator: n.validator
    }, null, 8, ["validator"]), wa("button", {
        class: "btn btn-blue",
        onClick: t[1] || (t[1] = (...e) => o.handleSubmit && o.handleSubmit(...e))
    }, [gp])])]), yp]), wa("div", bp, [wp, wa("div", Ep, [wa("div", Pp, [wa(s, {
        folderName: "social",
        img: "bitskins.svg",
        className: "bitskins"
    }), n.profile.link_bitskins ? (ha(), fa("div", kp, [wa("button", {
        class: "btn btn-blue",
        onClick: t[2] || (t[2] = (...e) => o.handleBitskinsUnlink && o.handleBitskinsUnlink(...e))
    }, [_p]), wa("p", null, [wa("a", {
        href: o.getBitskinsUrl(n.profile.steam_id),
        rel: "nofollow noopener",
        target: "_blank"
    }, u(o.getBitskinsUrl(n.profile.steam_id)), 9, ["href"])])])) : (ha(), fa("button", {
        key: 1,
        class: "btn btn-blue",
        onClick: t[3] || (t[3] = (...e) => o.handleBitskinsLink && o.handleBitskinsLink(...e))
    }, [Sp]))])])])]), wa(c)])) : _a("", !0)
};
var Cp = {
    props: {
        name: String,
        label: String,
        readonly: {
            type: String,
            default: null
        },
        disabled: {
            type: Boolean,
            default: null
        },
        icon: {
            type: String,
            default: null
        },
        type: {
            type: String,
            default: "text"
        },
        validator: {
            type: Object,
            default: null
        }
    },
    data: () => ({
        value: !1,
        errors: !1,
        edited: !1
    }),
    computed: {
        computed_value() {
            return this.validator && this.name ? this.validator.data[this.name] : this.value
        },
        error() {
            return !(!this.errors || !this.errors[0]) && this.errors[0].keyword
        },
        isEdited() {
            return this.checkErrors(), this.edited || this.validator?.force_validate
        },
        style() {
            return !(!this.isEdited || !this.name) && (this.errors ? "error" : "validated")
        }
    },
    methods: {
        checkErrors() {
            this.validator && this.name && (this.errors = this.validator.getErrors(this.name))
        },
        handleInputOnce() {
            this.edited = !0
        },
        parseValue(e) {
            return "number" === this.type ? "" === e ? null : Number(e) : e
        },
        handleInput(e) {
            this.validator && this.name ? (this.validator.set(this.name, e.target.checked), this.validator.validate(), this.checkErrors()) : this.$emit("update:modelValue", e.target.checked)
        },
        handleIconClick(e) {
            this.$emit("iconClick", e)
        }
    }
};
const Tp = {
        class: "checkbox-wrapper"
    },
    xp = {
        key: 0,
        class: "error-text"
    },
    Dp = wa("img", {
        src: Yc
    }, null, -1),
    Op = wa("div", {
        class: "checkmark"
    }, null, -1),
    Rp = {
        for: "check",
        class: "label"
    };
Cp.render = function(e, t, r, a, n, o) {
    return ha(), fa("label", Tp, [o.isEdited && n.errors ? (ha(), fa("span", xp, [Dp, Pa(u(o.error), 1)])) : _a("", !0), wa("input", {
        hidden: "",
        type: "checkbox",
        id: "check",
        name: r.name,
        onInput: t[1] || (t[1] = (...e) => o.handleInput && o.handleInput(...e)),
        onInputOnce: t[2] || (t[2] = (...e) => o.handleInputOnce && o.handleInputOnce(...e)),
        value: o.computed_value,
        readonly: r.readonly
    }, null, 40, ["name", "value", "readonly"]), Op, wa("span", Rp, u(r.label), 1)])
};
var Fp = {
    data: () => ({
        disabled: !1,
        hide_app_id: !1,
        block_trade_position: !1,
        amount: null,
        ban: null,
        show_profile: !1,
        profile: null,
        RateEnum: Gc,
        TradeTypeEnum: Qc,
        AppIdEnum: Xc,
        TradePositionEnum: Jc,
        PaymentMethodEnum: zc,
        validator: new nc("feedback", "create")
    }),
    setup() {
        const {
            addNotify: e
        } = bc;
        return {
            addNotify: e
        }
    },
    mounted() {
        this.load(this.$route.params.steam_id)
    },
    watch: {
        "$route.params.steam_id": function(e) {
            this.load(e)
        }
    },
    methods: {
        getAvatarPath: gc,
        async load(e) {
            this.profile = null, this.show_profile = !1, this.validator.set("to_steam_id", e), e && await this.handleProfileSearch(e)
        },
        async handleSubmit() {
            try {
                if (this.disabled) return void this.addNotify({
                    title: "Cooldown...",
                    type: "warning"
                });
                this.disabled = !0;
                const e = this.validator.data.to_steam_id,
                    t = this.validator.validate();
                this.validator.force();
                let r = null;
                t && this.profile && (r = await uc("feedback", "create", this.validator.data)), t && r ? (this.addNotify({
                    title: "Form accepted!",
                    content: "Your form was submitted successfully!",
                    type: "success"
                }), await this.$router.push(`/profile/${e}`)) : this.addNotify({
                    title: "Fix the form",
                    type: "error"
                })
            } catch (e) {
                2001 === e.error && this.addNotify({
                    title: "Cooldown...",
                    type: "warning"
                })
            } finally {
                setTimeout((() => {
                    this.disabled = !1
                }), 5e3)
            }
        },
        async handleProfileSearch() {
            const e = this.validator.data.to_steam_id;
            if (!e || this.validator.getErrors("to_steam_id") || this.profile?.steam_id === e) return;
            this.ban = !1, this.show_profile = !1, this.profile = !1;
            const {
                profile: t,
                ban: r
            } = await uc("feedback", "searchUser", {
                steam_id: e
            });
            t?.steam_id !== mc.data.session.steam_id ? (this.ban = r, this.profile = t, this.show_profile = !0) : this.addNotify({
                title: "Wrong profile",
                content: "You cannot add feedback to yourself",
                type: "error"
            })
        },
        async handleAmountChange(e) {
            e.target.checked && this.validator.set("amount", void 0)
        },
        async handleTradeTypeChange(e, t) {
            this.block_trade_position = !1, this.hide_app_id = !1, [5].includes(t) && (this.block_trade_position = !0, this.validator.set("trade_position", 2)), [3, 4].includes(t) && (this.hide_app_id = !0, this.validator.set("app_id", void 0))
        },
        handlePaste(e) {
            e.preventDefault();
            const t = e.clipboardData.getData("Text").replace(/\D/gi, "");
            return t.length > 0 && (this.validator.set("to_steam_id", t), this.validator.validate()), !1
        }
    },
    components: {
        ButtonGroup: lu,
        Input: qc,
        Checkbox: Cp,
        Message: nu,
        Footer: Md
    }
};
const $p = {
        id: "subpage-new_feedback",
        class: "subpage"
    },
    Ap = wa("div", {
        class: "page-heading"
    }, "New feedback", -1),
    Mp = {
        class: "content-wrapper"
    },
    Lp = {
        class: "user-info"
    },
    Np = {
        class: "steamid"
    },
    Ip = wa("div", {
        class: "title"
    }, "Steam user", -1),
    jp = {
        key: 0,
        class: "user-result"
    },
    Up = {
        key: 0
    },
    Hp = {
        key: 1
    },
    qp = {
        key: 2,
        class: "user-preview"
    },
    Yp = {
        class: "avatar"
    },
    Bp = {
        class: "description"
    },
    Wp = wa("div", {
        class: "title"
    }, "Description:", -1),
    Vp = {
        class: "links"
    },
    zp = wa("div", {
        class: "title"
    }, "Proof link (optional):", -1),
    Xp = {
        class: "details-select"
    },
    Qp = {
        class: "amount"
    },
    Gp = wa("div", {
        class: "title"
    }, "Trade value", -1),
    Kp = {
        class: "amount-wrapper"
    },
    Jp = {
        class: "send-feedback"
    },
    Zp = wa("span", {
        class: "text"
    }, "Send feedback", -1),
    ef = wa("span", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/send.svg"
    })], -1);

function tf(e) {
    if (null === e || !0 === e || !1 === e) return NaN;
    var t = Number(e);
    return isNaN(t) ? t : t < 0 ? Math.ceil(t) : Math.floor(t)
}

function rf(e, t) {
    if (t.length < e) throw new TypeError(e + " argument" + (e > 1 ? "s" : "") + " required, but only " + t.length + " present")
}

function af(e) {
    rf(1, arguments);
    var t = Object.prototype.toString.call(e);
    return e instanceof Date || "object" == typeof e && "[object Date]" === t ? new Date(e.getTime()) : "number" == typeof e || "[object Number]" === t ? new Date(e) : ("string" != typeof e && "[object String]" !== t || "undefined" == typeof console || (console.warn("Starting with v2.0.0-beta.1 date-fns doesn't accept strings as date arguments. Please use `parseISO` to parse strings. See: https://git.io/fjule"), console.warn((new Error).stack)), new Date(NaN))
}

function nf(e, t) {
    rf(2, arguments);
    var r = af(e),
        a = tf(t);
    return isNaN(a) ? new Date(NaN) : a ? (r.setDate(r.getDate() + a), r) : r
}

function of (e, t) {
    rf(2, arguments);
    var r = af(e),
        a = tf(t);
    if (isNaN(a)) return new Date(NaN);
    if (!a) return r;
    var n = r.getDate(),
        o = new Date(r.getTime());
    o.setMonth(r.getMonth() + a + 1, 0);
    var i = o.getDate();
    return n >= i ? o : (r.setFullYear(o.getFullYear(), o.getMonth(), n), r)
}

function sf(e, t) {
    rf(2, arguments);
    var r = af(e).getTime(),
        a = tf(t);
    return new Date(r + a)
}

function lf(e, t) {
    rf(1, arguments);
    var r = t || {},
        a = r.locale,
        n = a && a.options && a.options.weekStartsOn,
        o = null == n ? 0 : tf(n),
        i = null == r.weekStartsOn ? o : tf(r.weekStartsOn);
    if (!(i >= 0 && i <= 6)) throw new RangeError("weekStartsOn must be between 0 and 6 inclusively");
    var s = af(e),
        l = s.getDay(),
        c = (l < i ? 7 : 0) + l - i;
    return s.setDate(s.getDate() - c), s.setHours(0, 0, 0, 0), s
}
Fp.render = function(e, t, r, a, n, o) {
    const i = ta("Input"),
        s = ta("Message"),
        l = ta("ButtonGroup"),
        c = ta("Checkbox"),
        u = ta("Footer");
    return ha(), fa("div", $p, [Ap, wa("div", Mp, [wa("div", Lp, [wa("div", Np, [Ip, wa(i, {
        name: "to_steam_id",
        onBlur: o.handleProfileSearch,
        onPaste: o.handlePaste,
        validator: n.validator
    }, null, 8, ["onBlur", "onPaste", "validator"])]), n.show_profile ? (ha(), fa("div", jp, [n.ban ? (ha(), fa("div", Up, " This user is banned ")) : n.profile ? (ha(), fa("div", qp, [wa("div", Yp, [wa("img", {
        src: o.getAvatarPath(n.profile.avatar)
    }, null, 8, ["src"])]), wa("div", {
        class: "nickname",
        innerHTML: n.profile.username
    }, null, 8, ["innerHTML"])])) : (ha(), fa("div", Hp, " Profile not found :( "))])) : _a("", !0)]), wa("div", Bp, [Wp, wa(s, {
        name: "body",
        validator: n.validator
    }, null, 8, ["validator"])]), wa("div", Vp, [zp, wa(i, {
        name: "proof[0]",
        placeholder: "Proof link",
        validator: n.validator
    }, null, 8, ["validator"])]), wa("div", Xp, [wa(l, {
        options: n.RateEnum,
        class: "rate",
        name: "rate",
        title: "Rate",
        validator: n.validator
    }, null, 8, ["options", "validator"]), wa(l, {
        options: n.TradeTypeEnum,
        class: "trade_type",
        name: "trade_type",
        title: "Trade type",
        validator: n.validator,
        onChange: o.handleTradeTypeChange
    }, null, 8, ["options", "validator", "onChange"]), n.hide_app_id ? _a("", !0) : (ha(), fa(l, {
        key: 0,
        options: n.AppIdEnum,
        class: "game",
        name: "app_id",
        title: "Game",
        validator: n.validator
    }, null, 8, ["options", "validator"])), wa(l, {
        options: n.TradePositionEnum,
        class: "trade_order",
        name: "trade_position",
        title: "Trade order",
        validator: n.validator,
        disabled: n.block_trade_position
    }, null, 8, ["options", "validator", "disabled"]), wa(l, {
        options: n.PaymentMethodEnum,
        class: "payment_method",
        name: "payment_method",
        title: "Payment method",
        validator: n.validator
    }, null, 8, ["options", "validator"])]), wa("div", Qp, [Gp, wa("div", Kp, [wa(i, {
        class: "trade-value",
        placeholder: "$",
        name: "amount",
        type: "number",
        disabled: n.amount,
        validator: n.validator
    }, null, 8, ["disabled", "validator"]), wa(c, {
        modelValue: n.amount,
        "onUpdate:modelValue": t[1] || (t[1] = e => n.amount = e),
        label: "I prefer not to say",
        onChange: o.handleAmountChange
    }, null, 8, ["modelValue", "onChange"])])]), wa("div", Jp, [wa("button", {
        class: ["btn btn-blue hvr-bounce-to-right", {
            disabled: n.disabled || !n.validator.valid || !n.show_profile
        }],
        onClick: t[2] || (t[2] = (...e) => o.handleSubmit && o.handleSubmit(...e))
    }, [Zp, ef], 2)])]), wa(u)])
};

function cf(e) {
    return e.getTime() % 6e4
}

function uf(e) {
    var t = new Date(e.getTime()),
        r = Math.ceil(t.getTimezoneOffset());
    return t.setSeconds(0, 0), 6e4 * r + (r > 0 ? (6e4 + cf(t)) % 6e4 : cf(t))
}

function df(e) {
    rf(1, arguments);
    var t = af(e);
    return t.setHours(0, 0, 0, 0), t
}

function hf(e, t) {
    rf(2, arguments);
    var r = tf(t);
    return of(e, 12 * r)
}

function pf(e) {
    rf(1, arguments);
    var t = af(e);
    return !isNaN(t)
}

function ff(e, t) {
    rf(2, arguments);
    var r = df(e),
        a = df(t);
    return r.getTime() === a.getTime()
}

function mf(e) {
    rf(1, arguments);
    var t = af(e);
    return t.setDate(1), t.setHours(0, 0, 0, 0), t
}

function vf(e) {
    rf(1, arguments);
    var t = af(e),
        r = t.getMonth();
    return t.setFullYear(t.getFullYear(), r + 1, 0), t.setHours(23, 59, 59, 999), t
}

function gf(e, t) {
    rf(1, arguments);
    var r = t || {},
        a = r.locale,
        n = a && a.options && a.options.weekStartsOn,
        o = null == n ? 0 : tf(n),
        i = null == r.weekStartsOn ? o : tf(r.weekStartsOn);
    if (!(i >= 0 && i <= 6)) throw new RangeError("weekStartsOn must be between 0 and 6 inclusively");
    var s = af(e),
        l = s.getDay(),
        c = 6 + (l < i ? -7 : 0) - (l - i);
    return s.setDate(s.getDate() + c), s.setHours(23, 59, 59, 999), s
}
var yf = {
    lessThanXSeconds: {
        one: "less than a second",
        other: "less than {{count}} seconds"
    },
    xSeconds: {
        one: "1 second",
        other: "{{count}} seconds"
    },
    halfAMinute: "half a minute",
    lessThanXMinutes: {
        one: "less than a minute",
        other: "less than {{count}} minutes"
    },
    xMinutes: {
        one: "1 minute",
        other: "{{count}} minutes"
    },
    aboutXHours: {
        one: "about 1 hour",
        other: "about {{count}} hours"
    },
    xHours: {
        one: "1 hour",
        other: "{{count}} hours"
    },
    xDays: {
        one: "1 day",
        other: "{{count}} days"
    },
    aboutXWeeks: {
        one: "about 1 week",
        other: "about {{count}} weeks"
    },
    xWeeks: {
        one: "1 week",
        other: "{{count}} weeks"
    },
    aboutXMonths: {
        one: "about 1 month",
        other: "about {{count}} months"
    },
    xMonths: {
        one: "1 month",
        other: "{{count}} months"
    },
    aboutXYears: {
        one: "about 1 year",
        other: "about {{count}} years"
    },
    xYears: {
        one: "1 year",
        other: "{{count}} years"
    },
    overXYears: {
        one: "over 1 year",
        other: "over {{count}} years"
    },
    almostXYears: {
        one: "almost 1 year",
        other: "almost {{count}} years"
    }
};

function bf(e) {
    return function(t) {
        var r = t || {},
            a = r.width ? String(r.width) : e.defaultWidth;
        return e.formats[a] || e.formats[e.defaultWidth]
    }
}
var wf = {
        date: bf({
            formats: {
                full: "EEEE, MMMM do, y",
                long: "MMMM do, y",
                medium: "MMM d, y",
                short: "MM/dd/yyyy"
            },
            defaultWidth: "full"
        }),
        time: bf({
            formats: {
                full: "h:mm:ss a zzzz",
                long: "h:mm:ss a z",
                medium: "h:mm:ss a",
                short: "h:mm a"
            },
            defaultWidth: "full"
        }),
        dateTime: bf({
            formats: {
                full: "{{date}} 'at' {{time}}",
                long: "{{date}} 'at' {{time}}",
                medium: "{{date}}, {{time}}",
                short: "{{date}}, {{time}}"
            },
            defaultWidth: "full"
        })
    },
    Ef = {
        lastWeek: "'last' eeee 'at' p",
        yesterday: "'yesterday at' p",
        today: "'today at' p",
        tomorrow: "'tomorrow at' p",
        nextWeek: "eeee 'at' p",
        other: "P"
    };

function Pf(e) {
    return function(t, r) {
        var a, n = r || {};
        if ("formatting" === (n.context ? String(n.context) : "standalone") && e.formattingValues) {
            var o = e.defaultFormattingWidth || e.defaultWidth,
                i = n.width ? String(n.width) : o;
            a = e.formattingValues[i] || e.formattingValues[o]
        } else {
            var s = e.defaultWidth,
                l = n.width ? String(n.width) : e.defaultWidth;
            a = e.values[l] || e.values[s]
        }
        return a[e.argumentCallback ? e.argumentCallback(t) : t]
    }
}

function kf(e) {
    return function(t, r) {
        var a = String(t),
            n = r || {},
            o = n.width,
            i = o && e.matchPatterns[o] || e.matchPatterns[e.defaultMatchWidth],
            s = a.match(i);
        if (!s) return null;
        var l, c = s[0],
            u = o && e.parsePatterns[o] || e.parsePatterns[e.defaultParseWidth];
        return l = "[object Array]" === Object.prototype.toString.call(u) ? function(e, t) {
            for (var r = 0; r < e.length; r++)
                if (t(e[r])) return r
        }(u, (function(e) {
            return e.test(c)
        })) : function(e, t) {
            for (var r in e)
                if (e.hasOwnProperty(r) && t(e[r])) return r
        }(u, (function(e) {
            return e.test(c)
        })), l = e.valueCallback ? e.valueCallback(l) : l, {
            value: l = n.valueCallback ? n.valueCallback(l) : l,
            rest: a.slice(c.length)
        }
    }
}
var _f, Sf = {
    code: "en-US",
    formatDistance: function(e, t, r) {
        var a;
        return r = r || {}, a = "string" == typeof yf[e] ? yf[e] : 1 === t ? yf[e].one : yf[e].other.replace("{{count}}", t), r.addSuffix ? r.comparison > 0 ? "in " + a : a + " ago" : a
    },
    formatLong: wf,
    formatRelative: function(e, t, r, a) {
        return Ef[e]
    },
    localize: {
        ordinalNumber: function(e, t) {
            var r = Number(e),
                a = r % 100;
            if (a > 20 || a < 10) switch (a % 10) {
                case 1:
                    return r + "st";
                case 2:
                    return r + "nd";
                case 3:
                    return r + "rd"
            }
            return r + "th"
        },
        era: Pf({
            values: {
                narrow: ["B", "A"],
                abbreviated: ["BC", "AD"],
                wide: ["Before Christ", "Anno Domini"]
            },
            defaultWidth: "wide"
        }),
        quarter: Pf({
            values: {
                narrow: ["1", "2", "3", "4"],
                abbreviated: ["Q1", "Q2", "Q3", "Q4"],
                wide: ["1st quarter", "2nd quarter", "3rd quarter", "4th quarter"]
            },
            defaultWidth: "wide",
            argumentCallback: function(e) {
                return Number(e) - 1
            }
        }),
        month: Pf({
            values: {
                narrow: ["J", "F", "M", "A", "M", "J", "J", "A", "S", "O", "N", "D"],
                abbreviated: ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"],
                wide: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
            },
            defaultWidth: "wide"
        }),
        day: Pf({
            values: {
                narrow: ["S", "M", "T", "W", "T", "F", "S"],
                short: ["Su", "Mo", "Tu", "We", "Th", "Fr", "Sa"],
                abbreviated: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
                wide: ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]
            },
            defaultWidth: "wide"
        }),
        dayPeriod: Pf({
            values: {
                narrow: {
                    am: "a",
                    pm: "p",
                    midnight: "mi",
                    noon: "n",
                    morning: "morning",
                    afternoon: "afternoon",
                    evening: "evening",
                    night: "night"
                },
                abbreviated: {
                    am: "AM",
                    pm: "PM",
                    midnight: "midnight",
                    noon: "noon",
                    morning: "morning",
                    afternoon: "afternoon",
                    evening: "evening",
                    night: "night"
                },
                wide: {
                    am: "a.m.",
                    pm: "p.m.",
                    midnight: "midnight",
                    noon: "noon",
                    morning: "morning",
                    afternoon: "afternoon",
                    evening: "evening",
                    night: "night"
                }
            },
            defaultWidth: "wide",
            formattingValues: {
                narrow: {
                    am: "a",
                    pm: "p",
                    midnight: "mi",
                    noon: "n",
                    morning: "in the morning",
                    afternoon: "in the afternoon",
                    evening: "in the evening",
                    night: "at night"
                },
                abbreviated: {
                    am: "AM",
                    pm: "PM",
                    midnight: "midnight",
                    noon: "noon",
                    morning: "in the morning",
                    afternoon: "in the afternoon",
                    evening: "in the evening",
                    night: "at night"
                },
                wide: {
                    am: "a.m.",
                    pm: "p.m.",
                    midnight: "midnight",
                    noon: "noon",
                    morning: "in the morning",
                    afternoon: "in the afternoon",
                    evening: "in the evening",
                    night: "at night"
                }
            },
            defaultFormattingWidth: "wide"
        })
    },
    match: {
        ordinalNumber: (_f = {
            matchPattern: /^(\d+)(th|st|nd|rd)?/i,
            parsePattern: /\d+/i,
            valueCallback: function(e) {
                return parseInt(e, 10)
            }
        }, function(e, t) {
            var r = String(e),
                a = t || {},
                n = r.match(_f.matchPattern);
            if (!n) return null;
            var o = n[0],
                i = r.match(_f.parsePattern);
            if (!i) return null;
            var s = _f.valueCallback ? _f.valueCallback(i[0]) : i[0];
            return {
                value: s = a.valueCallback ? a.valueCallback(s) : s,
                rest: r.slice(o.length)
            }
        }),
        era: kf({
            matchPatterns: {
                narrow: /^(b|a)/i,
                abbreviated: /^(b\.?\s?c\.?|b\.?\s?c\.?\s?e\.?|a\.?\s?d\.?|c\.?\s?e\.?)/i,
                wide: /^(before christ|before common era|anno domini|common era)/i
            },
            defaultMatchWidth: "wide",
            parsePatterns: {
                any: [/^b/i, /^(a|c)/i]
            },
            defaultParseWidth: "any"
        }),
        quarter: kf({
            matchPatterns: {
                narrow: /^[1234]/i,
                abbreviated: /^q[1234]/i,
                wide: /^[1234](th|st|nd|rd)? quarter/i
            },
            defaultMatchWidth: "wide",
            parsePatterns: {
                any: [/1/i, /2/i, /3/i, /4/i]
            },
            defaultParseWidth: "any",
            valueCallback: function(e) {
                return e + 1
            }
        }),
        month: kf({
            matchPatterns: {
                narrow: /^[jfmasond]/i,
                abbreviated: /^(jan|feb|mar|apr|may|jun|jul|aug|sep|oct|nov|dec)/i,
                wide: /^(january|february|march|april|may|june|july|august|september|october|november|december)/i
            },
            defaultMatchWidth: "wide",
            parsePatterns: {
                narrow: [/^j/i, /^f/i, /^m/i, /^a/i, /^m/i, /^j/i, /^j/i, /^a/i, /^s/i, /^o/i, /^n/i, /^d/i],
                any: [/^ja/i, /^f/i, /^mar/i, /^ap/i, /^may/i, /^jun/i, /^jul/i, /^au/i, /^s/i, /^o/i, /^n/i, /^d/i]
            },
            defaultParseWidth: "any"
        }),
        day: kf({
            matchPatterns: {
                narrow: /^[smtwf]/i,
                short: /^(su|mo|tu|we|th|fr|sa)/i,
                abbreviated: /^(sun|mon|tue|wed|thu|fri|sat)/i,
                wide: /^(sunday|monday|tuesday|wednesday|thursday|friday|saturday)/i
            },
            defaultMatchWidth: "wide",
            parsePatterns: {
                narrow: [/^s/i, /^m/i, /^t/i, /^w/i, /^t/i, /^f/i, /^s/i],
                any: [/^su/i, /^m/i, /^tu/i, /^w/i, /^th/i, /^f/i, /^sa/i]
            },
            defaultParseWidth: "any"
        }),
        dayPeriod: kf({
            matchPatterns: {
                narrow: /^(a|p|mi|n|(in the|at) (morning|afternoon|evening|night))/i,
                any: /^([ap]\.?\s?m\.?|midnight|noon|(in the|at) (morning|afternoon|evening|night))/i
            },
            defaultMatchWidth: "any",
            parsePatterns: {
                any: {
                    am: /^a/i,
                    pm: /^p/i,
                    midnight: /^mi/i,
                    noon: /^no/i,
                    morning: /morning/i,
                    afternoon: /afternoon/i,
                    evening: /evening/i,
                    night: /night/i
                }
            },
            defaultParseWidth: "any"
        })
    },
    options: {
        weekStartsOn: 0,
        firstWeekContainsDate: 1
    }
};

function Cf(e, t) {
    rf(2, arguments);
    var r = tf(t);
    return sf(e, -r)
}

function Tf(e, t) {
    for (var r = e < 0 ? "-" : "", a = Math.abs(e).toString(); a.length < t;) a = "0" + a;
    return r + a
}
var xf = {
    y: function(e, t) {
        var r = e.getUTCFullYear(),
            a = r > 0 ? r : 1 - r;
        return Tf("yy" === t ? a % 100 : a, t.length)
    },
    M: function(e, t) {
        var r = e.getUTCMonth();
        return "M" === t ? String(r + 1) : Tf(r + 1, 2)
    },
    d: function(e, t) {
        return Tf(e.getUTCDate(), t.length)
    },
    a: function(e, t) {
        var r = e.getUTCHours() / 12 >= 1 ? "pm" : "am";
        switch (t) {
            case "a":
            case "aa":
            case "aaa":
                return r.toUpperCase();
            case "aaaaa":
                return r[0];
            case "aaaa":
            default:
                return "am" === r ? "a.m." : "p.m."
        }
    },
    h: function(e, t) {
        return Tf(e.getUTCHours() % 12 || 12, t.length)
    },
    H: function(e, t) {
        return Tf(e.getUTCHours(), t.length)
    },
    m: function(e, t) {
        return Tf(e.getUTCMinutes(), t.length)
    },
    s: function(e, t) {
        return Tf(e.getUTCSeconds(), t.length)
    },
    S: function(e, t) {
        var r = t.length,
            a = e.getUTCMilliseconds();
        return Tf(Math.floor(a * Math.pow(10, r - 3)), t.length)
    }
};

function Df(e) {
    rf(1, arguments);
    var t = 1,
        r = af(e),
        a = r.getUTCDay(),
        n = (a < t ? 7 : 0) + a - t;
    return r.setUTCDate(r.getUTCDate() - n), r.setUTCHours(0, 0, 0, 0), r
}

function Of(e) {
    rf(1, arguments);
    var t = af(e),
        r = t.getUTCFullYear(),
        a = new Date(0);
    a.setUTCFullYear(r + 1, 0, 4), a.setUTCHours(0, 0, 0, 0);
    var n = Df(a),
        o = new Date(0);
    o.setUTCFullYear(r, 0, 4), o.setUTCHours(0, 0, 0, 0);
    var i = Df(o);
    return t.getTime() >= n.getTime() ? r + 1 : t.getTime() >= i.getTime() ? r : r - 1
}

function Rf(e) {
    rf(1, arguments);
    var t = Of(e),
        r = new Date(0);
    r.setUTCFullYear(t, 0, 4), r.setUTCHours(0, 0, 0, 0);
    var a = Df(r);
    return a
}

function Ff(e) {
    rf(1, arguments);
    var t = af(e),
        r = Df(t).getTime() - Rf(t).getTime();
    return Math.round(r / 6048e5) + 1
}

function $f(e, t) {
    rf(1, arguments);
    var r = t || {},
        a = r.locale,
        n = a && a.options && a.options.weekStartsOn,
        o = null == n ? 0 : tf(n),
        i = null == r.weekStartsOn ? o : tf(r.weekStartsOn);
    if (!(i >= 0 && i <= 6)) throw new RangeError("weekStartsOn must be between 0 and 6 inclusively");
    var s = af(e),
        l = s.getUTCDay(),
        c = (l < i ? 7 : 0) + l - i;
    return s.setUTCDate(s.getUTCDate() - c), s.setUTCHours(0, 0, 0, 0), s
}

function Af(e, t) {
    rf(1, arguments);
    var r = af(e, t),
        a = r.getUTCFullYear(),
        n = t || {},
        o = n.locale,
        i = o && o.options && o.options.firstWeekContainsDate,
        s = null == i ? 1 : tf(i),
        l = null == n.firstWeekContainsDate ? s : tf(n.firstWeekContainsDate);
    if (!(l >= 1 && l <= 7)) throw new RangeError("firstWeekContainsDate must be between 1 and 7 inclusively");
    var c = new Date(0);
    c.setUTCFullYear(a + 1, 0, l), c.setUTCHours(0, 0, 0, 0);
    var u = $f(c, t),
        d = new Date(0);
    d.setUTCFullYear(a, 0, l), d.setUTCHours(0, 0, 0, 0);
    var h = $f(d, t);
    return r.getTime() >= u.getTime() ? a + 1 : r.getTime() >= h.getTime() ? a : a - 1
}

function Mf(e, t) {
    rf(1, arguments);
    var r = t || {},
        a = r.locale,
        n = a && a.options && a.options.firstWeekContainsDate,
        o = null == n ? 1 : tf(n),
        i = null == r.firstWeekContainsDate ? o : tf(r.firstWeekContainsDate),
        s = Af(e, t),
        l = new Date(0);
    l.setUTCFullYear(s, 0, i), l.setUTCHours(0, 0, 0, 0);
    var c = $f(l, t);
    return c
}

function Lf(e, t) {
    rf(1, arguments);
    var r = af(e),
        a = $f(r, t).getTime() - Mf(r, t).getTime();
    return Math.round(a / 6048e5) + 1
}
var Nf = "midnight",
    If = "noon",
    jf = "morning",
    Uf = "afternoon",
    Hf = "evening",
    qf = "night",
    Yf = {
        G: function(e, t, r) {
            var a = e.getUTCFullYear() > 0 ? 1 : 0;
            switch (t) {
                case "G":
                case "GG":
                case "GGG":
                    return r.era(a, {
                        width: "abbreviated"
                    });
                case "GGGGG":
                    return r.era(a, {
                        width: "narrow"
                    });
                case "GGGG":
                default:
                    return r.era(a, {
                        width: "wide"
                    })
            }
        },
        y: function(e, t, r) {
            if ("yo" === t) {
                var a = e.getUTCFullYear(),
                    n = a > 0 ? a : 1 - a;
                return r.ordinalNumber(n, {
                    unit: "year"
                })
            }
            return xf.y(e, t)
        },
        Y: function(e, t, r, a) {
            var n = Af(e, a),
                o = n > 0 ? n : 1 - n;
            return "YY" === t ? Tf(o % 100, 2) : "Yo" === t ? r.ordinalNumber(o, {
                unit: "year"
            }) : Tf(o, t.length)
        },
        R: function(e, t) {
            return Tf(Of(e), t.length)
        },
        u: function(e, t) {
            return Tf(e.getUTCFullYear(), t.length)
        },
        Q: function(e, t, r) {
            var a = Math.ceil((e.getUTCMonth() + 1) / 3);
            switch (t) {
                case "Q":
                    return String(a);
                case "QQ":
                    return Tf(a, 2);
                case "Qo":
                    return r.ordinalNumber(a, {
                        unit: "quarter"
                    });
                case "QQQ":
                    return r.quarter(a, {
                        width: "abbreviated",
                        context: "formatting"
                    });
                case "QQQQQ":
                    return r.quarter(a, {
                        width: "narrow",
                        context: "formatting"
                    });
                case "QQQQ":
                default:
                    return r.quarter(a, {
                        width: "wide",
                        context: "formatting"
                    })
            }
        },
        q: function(e, t, r) {
            var a = Math.ceil((e.getUTCMonth() + 1) / 3);
            switch (t) {
                case "q":
                    return String(a);
                case "qq":
                    return Tf(a, 2);
                case "qo":
                    return r.ordinalNumber(a, {
                        unit: "quarter"
                    });
                case "qqq":
                    return r.quarter(a, {
                        width: "abbreviated",
                        context: "standalone"
                    });
                case "qqqqq":
                    return r.quarter(a, {
                        width: "narrow",
                        context: "standalone"
                    });
                case "qqqq":
                default:
                    return r.quarter(a, {
                        width: "wide",
                        context: "standalone"
                    })
            }
        },
        M: function(e, t, r) {
            var a = e.getUTCMonth();
            switch (t) {
                case "M":
                case "MM":
                    return xf.M(e, t);
                case "Mo":
                    return r.ordinalNumber(a + 1, {
                        unit: "month"
                    });
                case "MMM":
                    return r.month(a, {
                        width: "abbreviated",
                        context: "formatting"
                    });
                case "MMMMM":
                    return r.month(a, {
                        width: "narrow",
                        context: "formatting"
                    });
                case "MMMM":
                default:
                    return r.month(a, {
                        width: "wide",
                        context: "formatting"
                    })
            }
        },
        L: function(e, t, r) {
            var a = e.getUTCMonth();
            switch (t) {
                case "L":
                    return String(a + 1);
                case "LL":
                    return Tf(a + 1, 2);
                case "Lo":
                    return r.ordinalNumber(a + 1, {
                        unit: "month"
                    });
                case "LLL":
                    return r.month(a, {
                        width: "abbreviated",
                        context: "standalone"
                    });
                case "LLLLL":
                    return r.month(a, {
                        width: "narrow",
                        context: "standalone"
                    });
                case "LLLL":
                default:
                    return r.month(a, {
                        width: "wide",
                        context: "standalone"
                    })
            }
        },
        w: function(e, t, r, a) {
            var n = Lf(e, a);
            return "wo" === t ? r.ordinalNumber(n, {
                unit: "week"
            }) : Tf(n, t.length)
        },
        I: function(e, t, r) {
            var a = Ff(e);
            return "Io" === t ? r.ordinalNumber(a, {
                unit: "week"
            }) : Tf(a, t.length)
        },
        d: function(e, t, r) {
            return "do" === t ? r.ordinalNumber(e.getUTCDate(), {
                unit: "date"
            }) : xf.d(e, t)
        },
        D: function(e, t, r) {
            var a = function(e) {
                rf(1, arguments);
                var t = af(e),
                    r = t.getTime();
                t.setUTCMonth(0, 1), t.setUTCHours(0, 0, 0, 0);
                var a = t.getTime(),
                    n = r - a;
                return Math.floor(n / 864e5) + 1
            }(e);
            return "Do" === t ? r.ordinalNumber(a, {
                unit: "dayOfYear"
            }) : Tf(a, t.length)
        },
        E: function(e, t, r) {
            var a = e.getUTCDay();
            switch (t) {
                case "E":
                case "EE":
                case "EEE":
                    return r.day(a, {
                        width: "abbreviated",
                        context: "formatting"
                    });
                case "EEEEE":
                    return r.day(a, {
                        width: "narrow",
                        context: "formatting"
                    });
                case "EEEEEE":
                    return r.day(a, {
                        width: "short",
                        context: "formatting"
                    });
                case "EEEE":
                default:
                    return r.day(a, {
                        width: "wide",
                        context: "formatting"
                    })
            }
        },
        e: function(e, t, r, a) {
            var n = e.getUTCDay(),
                o = (n - a.weekStartsOn + 8) % 7 || 7;
            switch (t) {
                case "e":
                    return String(o);
                case "ee":
                    return Tf(o, 2);
                case "eo":
                    return r.ordinalNumber(o, {
                        unit: "day"
                    });
                case "eee":
                    return r.day(n, {
                        width: "abbreviated",
                        context: "formatting"
                    });
                case "eeeee":
                    return r.day(n, {
                        width: "narrow",
                        context: "formatting"
                    });
                case "eeeeee":
                    return r.day(n, {
                        width: "short",
                        context: "formatting"
                    });
                case "eeee":
                default:
                    return r.day(n, {
                        width: "wide",
                        context: "formatting"
                    })
            }
        },
        c: function(e, t, r, a) {
            var n = e.getUTCDay(),
                o = (n - a.weekStartsOn + 8) % 7 || 7;
            switch (t) {
                case "c":
                    return String(o);
                case "cc":
                    return Tf(o, t.length);
                case "co":
                    return r.ordinalNumber(o, {
                        unit: "day"
                    });
                case "ccc":
                    return r.day(n, {
                        width: "abbreviated",
                        context: "standalone"
                    });
                case "ccccc":
                    return r.day(n, {
                        width: "narrow",
                        context: "standalone"
                    });
                case "cccccc":
                    return r.day(n, {
                        width: "short",
                        context: "standalone"
                    });
                case "cccc":
                default:
                    return r.day(n, {
                        width: "wide",
                        context: "standalone"
                    })
            }
        },
        i: function(e, t, r) {
            var a = e.getUTCDay(),
                n = 0 === a ? 7 : a;
            switch (t) {
                case "i":
                    return String(n);
                case "ii":
                    return Tf(n, t.length);
                case "io":
                    return r.ordinalNumber(n, {
                        unit: "day"
                    });
                case "iii":
                    return r.day(a, {
                        width: "abbreviated",
                        context: "formatting"
                    });
                case "iiiii":
                    return r.day(a, {
                        width: "narrow",
                        context: "formatting"
                    });
                case "iiiiii":
                    return r.day(a, {
                        width: "short",
                        context: "formatting"
                    });
                case "iiii":
                default:
                    return r.day(a, {
                        width: "wide",
                        context: "formatting"
                    })
            }
        },
        a: function(e, t, r) {
            var a = e.getUTCHours() / 12 >= 1 ? "pm" : "am";
            switch (t) {
                case "a":
                case "aa":
                case "aaa":
                    return r.dayPeriod(a, {
                        width: "abbreviated",
                        context: "formatting"
                    });
                case "aaaaa":
                    return r.dayPeriod(a, {
                        width: "narrow",
                        context: "formatting"
                    });
                case "aaaa":
                default:
                    return r.dayPeriod(a, {
                        width: "wide",
                        context: "formatting"
                    })
            }
        },
        b: function(e, t, r) {
            var a, n = e.getUTCHours();
            switch (a = 12 === n ? If : 0 === n ? Nf : n / 12 >= 1 ? "pm" : "am", t) {
                case "b":
                case "bb":
                case "bbb":
                    return r.dayPeriod(a, {
                        width: "abbreviated",
                        context: "formatting"
                    });
                case "bbbbb":
                    return r.dayPeriod(a, {
                        width: "narrow",
                        context: "formatting"
                    });
                case "bbbb":
                default:
                    return r.dayPeriod(a, {
                        width: "wide",
                        context: "formatting"
                    })
            }
        },
        B: function(e, t, r) {
            var a, n = e.getUTCHours();
            switch (a = n >= 17 ? Hf : n >= 12 ? Uf : n >= 4 ? jf : qf, t) {
                case "B":
                case "BB":
                case "BBB":
                    return r.dayPeriod(a, {
                        width: "abbreviated",
                        context: "formatting"
                    });
                case "BBBBB":
                    return r.dayPeriod(a, {
                        width: "narrow",
                        context: "formatting"
                    });
                case "BBBB":
                default:
                    return r.dayPeriod(a, {
                        width: "wide",
                        context: "formatting"
                    })
            }
        },
        h: function(e, t, r) {
            if ("ho" === t) {
                var a = e.getUTCHours() % 12;
                return 0 === a && (a = 12), r.ordinalNumber(a, {
                    unit: "hour"
                })
            }
            return xf.h(e, t)
        },
        H: function(e, t, r) {
            return "Ho" === t ? r.ordinalNumber(e.getUTCHours(), {
                unit: "hour"
            }) : xf.H(e, t)
        },
        K: function(e, t, r) {
            var a = e.getUTCHours() % 12;
            return "Ko" === t ? r.ordinalNumber(a, {
                unit: "hour"
            }) : Tf(a, t.length)
        },
        k: function(e, t, r) {
            var a = e.getUTCHours();
            return 0 === a && (a = 24), "ko" === t ? r.ordinalNumber(a, {
                unit: "hour"
            }) : Tf(a, t.length)
        },
        m: function(e, t, r) {
            return "mo" === t ? r.ordinalNumber(e.getUTCMinutes(), {
                unit: "minute"
            }) : xf.m(e, t)
        },
        s: function(e, t, r) {
            return "so" === t ? r.ordinalNumber(e.getUTCSeconds(), {
                unit: "second"
            }) : xf.s(e, t)
        },
        S: function(e, t) {
            return xf.S(e, t)
        },
        X: function(e, t, r, a) {
            var n = (a._originalDate || e).getTimezoneOffset();
            if (0 === n) return "Z";
            switch (t) {
                case "X":
                    return Wf(n);
                case "XXXX":
                case "XX":
                    return Vf(n);
                case "XXXXX":
                case "XXX":
                default:
                    return Vf(n, ":")
            }
        },
        x: function(e, t, r, a) {
            var n = (a._originalDate || e).getTimezoneOffset();
            switch (t) {
                case "x":
                    return Wf(n);
                case "xxxx":
                case "xx":
                    return Vf(n);
                case "xxxxx":
                case "xxx":
                default:
                    return Vf(n, ":")
            }
        },
        O: function(e, t, r, a) {
            var n = (a._originalDate || e).getTimezoneOffset();
            switch (t) {
                case "O":
                case "OO":
                case "OOO":
                    return "GMT" + Bf(n, ":");
                case "OOOO":
                default:
                    return "GMT" + Vf(n, ":")
            }
        },
        z: function(e, t, r, a) {
            var n = (a._originalDate || e).getTimezoneOffset();
            switch (t) {
                case "z":
                case "zz":
                case "zzz":
                    return "GMT" + Bf(n, ":");
                case "zzzz":
                default:
                    return "GMT" + Vf(n, ":")
            }
        },
        t: function(e, t, r, a) {
            var n = a._originalDate || e;
            return Tf(Math.floor(n.getTime() / 1e3), t.length)
        },
        T: function(e, t, r, a) {
            return Tf((a._originalDate || e).getTime(), t.length)
        }
    };

function Bf(e, t) {
    var r = e > 0 ? "-" : "+",
        a = Math.abs(e),
        n = Math.floor(a / 60),
        o = a % 60;
    if (0 === o) return r + String(n);
    var i = t || "";
    return r + String(n) + i + Tf(o, 2)
}

function Wf(e, t) {
    return e % 60 == 0 ? (e > 0 ? "-" : "+") + Tf(Math.abs(e) / 60, 2) : Vf(e, t)
}

function Vf(e, t) {
    var r = t || "",
        a = e > 0 ? "-" : "+",
        n = Math.abs(e);
    return a + Tf(Math.floor(n / 60), 2) + r + Tf(n % 60, 2)
}

function zf(e, t) {
    switch (e) {
        case "P":
            return t.date({
                width: "short"
            });
        case "PP":
            return t.date({
                width: "medium"
            });
        case "PPP":
            return t.date({
                width: "long"
            });
        case "PPPP":
        default:
            return t.date({
                width: "full"
            })
    }
}

function Xf(e, t) {
    switch (e) {
        case "p":
            return t.time({
                width: "short"
            });
        case "pp":
            return t.time({
                width: "medium"
            });
        case "ppp":
            return t.time({
                width: "long"
            });
        case "pppp":
        default:
            return t.time({
                width: "full"
            })
    }
}
var Qf = {
        p: Xf,
        P: function(e, t) {
            var r, a = e.match(/(P+)(p+)?/),
                n = a[1],
                o = a[2];
            if (!o) return zf(e, t);
            switch (n) {
                case "P":
                    r = t.dateTime({
                        width: "short"
                    });
                    break;
                case "PP":
                    r = t.dateTime({
                        width: "medium"
                    });
                    break;
                case "PPP":
                    r = t.dateTime({
                        width: "long"
                    });
                    break;
                case "PPPP":
                default:
                    r = t.dateTime({
                        width: "full"
                    })
            }
            return r.replace("{{date}}", zf(n, t)).replace("{{time}}", Xf(o, t))
        }
    },
    Gf = ["D", "DD"],
    Kf = ["YY", "YYYY"];

function Jf(e) {
    return -1 !== Gf.indexOf(e)
}

function Zf(e) {
    return -1 !== Kf.indexOf(e)
}

function em(e, t, r) {
    if ("YYYY" === e) throw new RangeError("Use `yyyy` instead of `YYYY` (in `".concat(t, "`) for formatting years to the input `").concat(r, "`; see: https://git.io/fxCyr"));
    if ("YY" === e) throw new RangeError("Use `yy` instead of `YY` (in `".concat(t, "`) for formatting years to the input `").concat(r, "`; see: https://git.io/fxCyr"));
    if ("D" === e) throw new RangeError("Use `d` instead of `D` (in `".concat(t, "`) for formatting days of the month to the input `").concat(r, "`; see: https://git.io/fxCyr"));
    if ("DD" === e) throw new RangeError("Use `dd` instead of `DD` (in `".concat(t, "`) for formatting days of the month to the input `").concat(r, "`; see: https://git.io/fxCyr"))
}
var tm = /[yYQqMLwIdDecihHKkms]o|(\w)\1*|''|'(''|[^'])+('|$)|./g,
    rm = /P+p+|P+|p+|''|'(''|[^'])+('|$)|./g,
    am = /^'([^]*?)'?$/,
    nm = /''/g,
    om = /[a-zA-Z]/;

function im(e) {
    return e.match(am)[1].replace(nm, "'")
}

function sm(e, t) {
    if (null == e) throw new TypeError("assign requires that input parameter not be null or undefined");
    for (var r in t = t || {}) t.hasOwnProperty(r) && (e[r] = t[r]);
    return e
}

function lm(e) {
    rf(1, arguments);
    var t = af(e),
        r = t.getFullYear(),
        a = 10 * Math.floor(r / 10);
    return a
}

function cm(e) {
    rf(1, arguments);
    var t = af(e),
        r = t.getFullYear();
    return r
}

function um(e, t) {
    rf(2, arguments);
    var r = af(e),
        a = af(t);
    return r.getTime() > a.getTime()
}

function dm(e, t) {
    rf(2, arguments);
    var r = af(e),
        a = af(t);
    return r.getTime() < a.getTime()
}

function hm(e, t, r) {
    rf(2, arguments);
    var a = r || {},
        n = a.locale,
        o = n && n.options && n.options.weekStartsOn,
        i = null == o ? 0 : tf(o),
        s = null == a.weekStartsOn ? i : tf(a.weekStartsOn);
    if (!(s >= 0 && s <= 6)) throw new RangeError("weekStartsOn must be between 0 and 6 inclusively");
    var l = af(e),
        c = tf(t),
        u = l.getUTCDay(),
        d = c % 7,
        h = (d + 7) % 7,
        p = (h < s ? 7 : 0) + c - u;
    return l.setUTCDate(l.getUTCDate() + p), l
}
var pm = /^(1[0-2]|0?\d)/,
    fm = /^(3[0-1]|[0-2]?\d)/,
    mm = /^(36[0-6]|3[0-5]\d|[0-2]?\d?\d)/,
    vm = /^(5[0-3]|[0-4]?\d)/,
    gm = /^(2[0-3]|[0-1]?\d)/,
    ym = /^(2[0-4]|[0-1]?\d)/,
    bm = /^(1[0-1]|0?\d)/,
    wm = /^(1[0-2]|0?\d)/,
    Em = /^[0-5]?\d/,
    Pm = /^[0-5]?\d/,
    km = /^\d/,
    _m = /^\d{1,2}/,
    Sm = /^\d{1,3}/,
    Cm = /^\d{1,4}/,
    Tm = /^-?\d+/,
    xm = /^-?\d/,
    Dm = /^-?\d{1,2}/,
    Om = /^-?\d{1,3}/,
    Rm = /^-?\d{1,4}/,
    Fm = /^([+-])(\d{2})(\d{2})?|Z/,
    $m = /^([+-])(\d{2})(\d{2})|Z/,
    Am = /^([+-])(\d{2})(\d{2})((\d{2}))?|Z/,
    Mm = /^([+-])(\d{2}):(\d{2})|Z/,
    Lm = /^([+-])(\d{2}):(\d{2})(:(\d{2}))?|Z/;

function Nm(e, t, r) {
    var a = t.match(e);
    if (!a) return null;
    var n = parseInt(a[0], 10);
    return {
        value: r ? r(n) : n,
        rest: t.slice(a[0].length)
    }
}

function Im(e, t) {
    var r = t.match(e);
    return r ? "Z" === r[0] ? {
        value: 0,
        rest: t.slice(1)
    } : {
        value: ("+" === r[1] ? 1 : -1) * (36e5 * (r[2] ? parseInt(r[2], 10) : 0) + 6e4 * (r[3] ? parseInt(r[3], 10) : 0) + 1e3 * (r[5] ? parseInt(r[5], 10) : 0)),
        rest: t.slice(r[0].length)
    } : null
}

function jm(e, t) {
    return Nm(Tm, e, t)
}

function Um(e, t, r) {
    switch (e) {
        case 1:
            return Nm(km, t, r);
        case 2:
            return Nm(_m, t, r);
        case 3:
            return Nm(Sm, t, r);
        case 4:
            return Nm(Cm, t, r);
        default:
            return Nm(new RegExp("^\\d{1," + e + "}"), t, r)
    }
}

function Hm(e, t, r) {
    switch (e) {
        case 1:
            return Nm(xm, t, r);
        case 2:
            return Nm(Dm, t, r);
        case 3:
            return Nm(Om, t, r);
        case 4:
            return Nm(Rm, t, r);
        default:
            return Nm(new RegExp("^-?\\d{1," + e + "}"), t, r)
    }
}

function qm(e) {
    switch (e) {
        case "morning":
            return 4;
        case "evening":
            return 17;
        case "pm":
        case "noon":
        case "afternoon":
            return 12;
        case "am":
        case "midnight":
        case "night":
        default:
            return 0
    }
}

function Ym(e, t) {
    var r, a = t > 0,
        n = a ? t : 1 - t;
    if (n <= 50) r = e || 100;
    else {
        var o = n + 50;
        r = e + 100 * Math.floor(o / 100) - (e >= o % 100 ? 100 : 0)
    }
    return a ? r : 1 - r
}
var Bm = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31],
    Wm = [31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];

function Vm(e) {
    return e % 400 == 0 || e % 4 == 0 && e % 100 != 0
}
var zm = {
        G: {
            priority: 140,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "G":
                    case "GG":
                    case "GGG":
                        return r.era(e, {
                            width: "abbreviated"
                        }) || r.era(e, {
                            width: "narrow"
                        });
                    case "GGGGG":
                        return r.era(e, {
                            width: "narrow"
                        });
                    case "GGGG":
                    default:
                        return r.era(e, {
                            width: "wide"
                        }) || r.era(e, {
                            width: "abbreviated"
                        }) || r.era(e, {
                            width: "narrow"
                        })
                }
            },
            set: function(e, t, r, a) {
                return t.era = r, e.setUTCFullYear(r, 0, 1), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["R", "u", "t", "T"]
        },
        y: {
            priority: 130,
            parse: function(e, t, r, a) {
                var n = function(e) {
                    return {
                        year: e,
                        isTwoDigitYear: "yy" === t
                    }
                };
                switch (t) {
                    case "y":
                        return Um(4, e, n);
                    case "yo":
                        return r.ordinalNumber(e, {
                            unit: "year",
                            valueCallback: n
                        });
                    default:
                        return Um(t.length, e, n)
                }
            },
            validate: function(e, t, r) {
                return t.isTwoDigitYear || t.year > 0
            },
            set: function(e, t, r, a) {
                var n = e.getUTCFullYear();
                if (r.isTwoDigitYear) {
                    var o = Ym(r.year, n);
                    return e.setUTCFullYear(o, 0, 1), e.setUTCHours(0, 0, 0, 0), e
                }
                var i = "era" in t && 1 !== t.era ? 1 - r.year : r.year;
                return e.setUTCFullYear(i, 0, 1), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["Y", "R", "u", "w", "I", "i", "e", "c", "t", "T"]
        },
        Y: {
            priority: 130,
            parse: function(e, t, r, a) {
                var n = function(e) {
                    return {
                        year: e,
                        isTwoDigitYear: "YY" === t
                    }
                };
                switch (t) {
                    case "Y":
                        return Um(4, e, n);
                    case "Yo":
                        return r.ordinalNumber(e, {
                            unit: "year",
                            valueCallback: n
                        });
                    default:
                        return Um(t.length, e, n)
                }
            },
            validate: function(e, t, r) {
                return t.isTwoDigitYear || t.year > 0
            },
            set: function(e, t, r, a) {
                var n = Af(e, a);
                if (r.isTwoDigitYear) {
                    var o = Ym(r.year, n);
                    return e.setUTCFullYear(o, 0, a.firstWeekContainsDate), e.setUTCHours(0, 0, 0, 0), $f(e, a)
                }
                var i = "era" in t && 1 !== t.era ? 1 - r.year : r.year;
                return e.setUTCFullYear(i, 0, a.firstWeekContainsDate), e.setUTCHours(0, 0, 0, 0), $f(e, a)
            },
            incompatibleTokens: ["y", "R", "u", "Q", "q", "M", "L", "I", "d", "D", "i", "t", "T"]
        },
        R: {
            priority: 130,
            parse: function(e, t, r, a) {
                return Hm("R" === t ? 4 : t.length, e)
            },
            set: function(e, t, r, a) {
                var n = new Date(0);
                return n.setUTCFullYear(r, 0, 4), n.setUTCHours(0, 0, 0, 0), Df(n)
            },
            incompatibleTokens: ["G", "y", "Y", "u", "Q", "q", "M", "L", "w", "d", "D", "e", "c", "t", "T"]
        },
        u: {
            priority: 130,
            parse: function(e, t, r, a) {
                return Hm("u" === t ? 4 : t.length, e)
            },
            set: function(e, t, r, a) {
                return e.setUTCFullYear(r, 0, 1), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["G", "y", "Y", "R", "w", "I", "i", "e", "c", "t", "T"]
        },
        Q: {
            priority: 120,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "Q":
                    case "QQ":
                        return Um(t.length, e);
                    case "Qo":
                        return r.ordinalNumber(e, {
                            unit: "quarter"
                        });
                    case "QQQ":
                        return r.quarter(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.quarter(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "QQQQQ":
                        return r.quarter(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "QQQQ":
                    default:
                        return r.quarter(e, {
                            width: "wide",
                            context: "formatting"
                        }) || r.quarter(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.quarter(e, {
                            width: "narrow",
                            context: "formatting"
                        })
                }
            },
            validate: function(e, t, r) {
                return t >= 1 && t <= 4
            },
            set: function(e, t, r, a) {
                return e.setUTCMonth(3 * (r - 1), 1), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["Y", "R", "q", "M", "L", "w", "I", "d", "D", "i", "e", "c", "t", "T"]
        },
        q: {
            priority: 120,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "q":
                    case "qq":
                        return Um(t.length, e);
                    case "qo":
                        return r.ordinalNumber(e, {
                            unit: "quarter"
                        });
                    case "qqq":
                        return r.quarter(e, {
                            width: "abbreviated",
                            context: "standalone"
                        }) || r.quarter(e, {
                            width: "narrow",
                            context: "standalone"
                        });
                    case "qqqqq":
                        return r.quarter(e, {
                            width: "narrow",
                            context: "standalone"
                        });
                    case "qqqq":
                    default:
                        return r.quarter(e, {
                            width: "wide",
                            context: "standalone"
                        }) || r.quarter(e, {
                            width: "abbreviated",
                            context: "standalone"
                        }) || r.quarter(e, {
                            width: "narrow",
                            context: "standalone"
                        })
                }
            },
            validate: function(e, t, r) {
                return t >= 1 && t <= 4
            },
            set: function(e, t, r, a) {
                return e.setUTCMonth(3 * (r - 1), 1), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["Y", "R", "Q", "M", "L", "w", "I", "d", "D", "i", "e", "c", "t", "T"]
        },
        M: {
            priority: 110,
            parse: function(e, t, r, a) {
                var n = function(e) {
                    return e - 1
                };
                switch (t) {
                    case "M":
                        return Nm(pm, e, n);
                    case "MM":
                        return Um(2, e, n);
                    case "Mo":
                        return r.ordinalNumber(e, {
                            unit: "month",
                            valueCallback: n
                        });
                    case "MMM":
                        return r.month(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.month(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "MMMMM":
                        return r.month(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "MMMM":
                    default:
                        return r.month(e, {
                            width: "wide",
                            context: "formatting"
                        }) || r.month(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.month(e, {
                            width: "narrow",
                            context: "formatting"
                        })
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 11
            },
            set: function(e, t, r, a) {
                return e.setUTCMonth(r, 1), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["Y", "R", "q", "Q", "L", "w", "I", "D", "i", "e", "c", "t", "T"]
        },
        L: {
            priority: 110,
            parse: function(e, t, r, a) {
                var n = function(e) {
                    return e - 1
                };
                switch (t) {
                    case "L":
                        return Nm(pm, e, n);
                    case "LL":
                        return Um(2, e, n);
                    case "Lo":
                        return r.ordinalNumber(e, {
                            unit: "month",
                            valueCallback: n
                        });
                    case "LLL":
                        return r.month(e, {
                            width: "abbreviated",
                            context: "standalone"
                        }) || r.month(e, {
                            width: "narrow",
                            context: "standalone"
                        });
                    case "LLLLL":
                        return r.month(e, {
                            width: "narrow",
                            context: "standalone"
                        });
                    case "LLLL":
                    default:
                        return r.month(e, {
                            width: "wide",
                            context: "standalone"
                        }) || r.month(e, {
                            width: "abbreviated",
                            context: "standalone"
                        }) || r.month(e, {
                            width: "narrow",
                            context: "standalone"
                        })
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 11
            },
            set: function(e, t, r, a) {
                return e.setUTCMonth(r, 1), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["Y", "R", "q", "Q", "M", "w", "I", "D", "i", "e", "c", "t", "T"]
        },
        w: {
            priority: 100,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "w":
                        return Nm(vm, e);
                    case "wo":
                        return r.ordinalNumber(e, {
                            unit: "week"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return t >= 1 && t <= 53
            },
            set: function(e, t, r, a) {
                return $f(function(e, t, r) {
                    rf(2, arguments);
                    var a = af(e),
                        n = tf(t),
                        o = Lf(a, r) - n;
                    return a.setUTCDate(a.getUTCDate() - 7 * o), a
                }(e, r, a), a)
            },
            incompatibleTokens: ["y", "R", "u", "q", "Q", "M", "L", "I", "d", "D", "i", "t", "T"]
        },
        I: {
            priority: 100,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "I":
                        return Nm(vm, e);
                    case "Io":
                        return r.ordinalNumber(e, {
                            unit: "week"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return t >= 1 && t <= 53
            },
            set: function(e, t, r, a) {
                return Df(function(e, t) {
                    rf(2, arguments);
                    var r = af(e),
                        a = tf(t),
                        n = Ff(r) - a;
                    return r.setUTCDate(r.getUTCDate() - 7 * n), r
                }(e, r, a), a)
            },
            incompatibleTokens: ["y", "Y", "u", "q", "Q", "M", "L", "w", "d", "D", "e", "c", "t", "T"]
        },
        d: {
            priority: 90,
            subPriority: 1,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "d":
                        return Nm(fm, e);
                    case "do":
                        return r.ordinalNumber(e, {
                            unit: "date"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                var a = Vm(e.getUTCFullYear()),
                    n = e.getUTCMonth();
                return a ? t >= 1 && t <= Wm[n] : t >= 1 && t <= Bm[n]
            },
            set: function(e, t, r, a) {
                return e.setUTCDate(r), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["Y", "R", "q", "Q", "w", "I", "D", "i", "e", "c", "t", "T"]
        },
        D: {
            priority: 90,
            subPriority: 1,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "D":
                    case "DD":
                        return Nm(mm, e);
                    case "Do":
                        return r.ordinalNumber(e, {
                            unit: "date"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return Vm(e.getUTCFullYear()) ? t >= 1 && t <= 366 : t >= 1 && t <= 365
            },
            set: function(e, t, r, a) {
                return e.setUTCMonth(0, r), e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["Y", "R", "q", "Q", "M", "L", "w", "I", "d", "E", "i", "e", "c", "t", "T"]
        },
        E: {
            priority: 90,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "E":
                    case "EE":
                    case "EEE":
                        return r.day(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "short",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "EEEEE":
                        return r.day(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "EEEEEE":
                        return r.day(e, {
                            width: "short",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "EEEE":
                    default:
                        return r.day(e, {
                            width: "wide",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "short",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting"
                        })
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 6
            },
            set: function(e, t, r, a) {
                return (e = hm(e, r, a)).setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["D", "i", "e", "c", "t", "T"]
        },
        e: {
            priority: 90,
            parse: function(e, t, r, a) {
                var n = function(e) {
                    var t = 7 * Math.floor((e - 1) / 7);
                    return (e + a.weekStartsOn + 6) % 7 + t
                };
                switch (t) {
                    case "e":
                    case "ee":
                        return Um(t.length, e, n);
                    case "eo":
                        return r.ordinalNumber(e, {
                            unit: "day",
                            valueCallback: n
                        });
                    case "eee":
                        return r.day(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "short",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "eeeee":
                        return r.day(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "eeeeee":
                        return r.day(e, {
                            width: "short",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "eeee":
                    default:
                        return r.day(e, {
                            width: "wide",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "short",
                            context: "formatting"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting"
                        })
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 6
            },
            set: function(e, t, r, a) {
                return (e = hm(e, r, a)).setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["y", "R", "u", "q", "Q", "M", "L", "I", "d", "D", "E", "i", "c", "t", "T"]
        },
        c: {
            priority: 90,
            parse: function(e, t, r, a) {
                var n = function(e) {
                    var t = 7 * Math.floor((e - 1) / 7);
                    return (e + a.weekStartsOn + 6) % 7 + t
                };
                switch (t) {
                    case "c":
                    case "cc":
                        return Um(t.length, e, n);
                    case "co":
                        return r.ordinalNumber(e, {
                            unit: "day",
                            valueCallback: n
                        });
                    case "ccc":
                        return r.day(e, {
                            width: "abbreviated",
                            context: "standalone"
                        }) || r.day(e, {
                            width: "short",
                            context: "standalone"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "standalone"
                        });
                    case "ccccc":
                        return r.day(e, {
                            width: "narrow",
                            context: "standalone"
                        });
                    case "cccccc":
                        return r.day(e, {
                            width: "short",
                            context: "standalone"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "standalone"
                        });
                    case "cccc":
                    default:
                        return r.day(e, {
                            width: "wide",
                            context: "standalone"
                        }) || r.day(e, {
                            width: "abbreviated",
                            context: "standalone"
                        }) || r.day(e, {
                            width: "short",
                            context: "standalone"
                        }) || r.day(e, {
                            width: "narrow",
                            context: "standalone"
                        })
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 6
            },
            set: function(e, t, r, a) {
                return (e = hm(e, r, a)).setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["y", "R", "u", "q", "Q", "M", "L", "I", "d", "D", "E", "i", "e", "t", "T"]
        },
        i: {
            priority: 90,
            parse: function(e, t, r, a) {
                var n = function(e) {
                    return 0 === e ? 7 : e
                };
                switch (t) {
                    case "i":
                    case "ii":
                        return Um(t.length, e);
                    case "io":
                        return r.ordinalNumber(e, {
                            unit: "day"
                        });
                    case "iii":
                        return r.day(e, {
                            width: "abbreviated",
                            context: "formatting",
                            valueCallback: n
                        }) || r.day(e, {
                            width: "short",
                            context: "formatting",
                            valueCallback: n
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting",
                            valueCallback: n
                        });
                    case "iiiii":
                        return r.day(e, {
                            width: "narrow",
                            context: "formatting",
                            valueCallback: n
                        });
                    case "iiiiii":
                        return r.day(e, {
                            width: "short",
                            context: "formatting",
                            valueCallback: n
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting",
                            valueCallback: n
                        });
                    case "iiii":
                    default:
                        return r.day(e, {
                            width: "wide",
                            context: "formatting",
                            valueCallback: n
                        }) || r.day(e, {
                            width: "abbreviated",
                            context: "formatting",
                            valueCallback: n
                        }) || r.day(e, {
                            width: "short",
                            context: "formatting",
                            valueCallback: n
                        }) || r.day(e, {
                            width: "narrow",
                            context: "formatting",
                            valueCallback: n
                        })
                }
            },
            validate: function(e, t, r) {
                return t >= 1 && t <= 7
            },
            set: function(e, t, r, a) {
                return (e = function(e, t) {
                    rf(2, arguments);
                    var r = tf(t);
                    r % 7 == 0 && (r -= 7);
                    var a = 1,
                        n = af(e),
                        o = n.getUTCDay(),
                        i = ((r % 7 + 7) % 7 < a ? 7 : 0) + r - o;
                    return n.setUTCDate(n.getUTCDate() + i), n
                }(e, r, a)).setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["y", "Y", "u", "q", "Q", "M", "L", "w", "d", "D", "E", "e", "c", "t", "T"]
        },
        a: {
            priority: 80,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "a":
                    case "aa":
                    case "aaa":
                        return r.dayPeriod(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "aaaaa":
                        return r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "aaaa":
                    default:
                        return r.dayPeriod(e, {
                            width: "wide",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        })
                }
            },
            set: function(e, t, r, a) {
                return e.setUTCHours(qm(r), 0, 0, 0), e
            },
            incompatibleTokens: ["b", "B", "H", "K", "k", "t", "T"]
        },
        b: {
            priority: 80,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "b":
                    case "bb":
                    case "bbb":
                        return r.dayPeriod(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "bbbbb":
                        return r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "bbbb":
                    default:
                        return r.dayPeriod(e, {
                            width: "wide",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        })
                }
            },
            set: function(e, t, r, a) {
                return e.setUTCHours(qm(r), 0, 0, 0), e
            },
            incompatibleTokens: ["a", "B", "H", "K", "k", "t", "T"]
        },
        B: {
            priority: 80,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "B":
                    case "BB":
                    case "BBB":
                        return r.dayPeriod(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "BBBBB":
                        return r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        });
                    case "BBBB":
                    default:
                        return r.dayPeriod(e, {
                            width: "wide",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "abbreviated",
                            context: "formatting"
                        }) || r.dayPeriod(e, {
                            width: "narrow",
                            context: "formatting"
                        })
                }
            },
            set: function(e, t, r, a) {
                return e.setUTCHours(qm(r), 0, 0, 0), e
            },
            incompatibleTokens: ["a", "b", "t", "T"]
        },
        h: {
            priority: 70,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "h":
                        return Nm(wm, e);
                    case "ho":
                        return r.ordinalNumber(e, {
                            unit: "hour"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return t >= 1 && t <= 12
            },
            set: function(e, t, r, a) {
                var n = e.getUTCHours() >= 12;
                return n && r < 12 ? e.setUTCHours(r + 12, 0, 0, 0) : n || 12 !== r ? e.setUTCHours(r, 0, 0, 0) : e.setUTCHours(0, 0, 0, 0), e
            },
            incompatibleTokens: ["H", "K", "k", "t", "T"]
        },
        H: {
            priority: 70,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "H":
                        return Nm(gm, e);
                    case "Ho":
                        return r.ordinalNumber(e, {
                            unit: "hour"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 23
            },
            set: function(e, t, r, a) {
                return e.setUTCHours(r, 0, 0, 0), e
            },
            incompatibleTokens: ["a", "b", "h", "K", "k", "t", "T"]
        },
        K: {
            priority: 70,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "K":
                        return Nm(bm, e);
                    case "Ko":
                        return r.ordinalNumber(e, {
                            unit: "hour"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 11
            },
            set: function(e, t, r, a) {
                return e.getUTCHours() >= 12 && r < 12 ? e.setUTCHours(r + 12, 0, 0, 0) : e.setUTCHours(r, 0, 0, 0), e
            },
            incompatibleTokens: ["a", "b", "h", "H", "k", "t", "T"]
        },
        k: {
            priority: 70,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "k":
                        return Nm(ym, e);
                    case "ko":
                        return r.ordinalNumber(e, {
                            unit: "hour"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return t >= 1 && t <= 24
            },
            set: function(e, t, r, a) {
                var n = r <= 24 ? r % 24 : r;
                return e.setUTCHours(n, 0, 0, 0), e
            },
            incompatibleTokens: ["a", "b", "h", "H", "K", "t", "T"]
        },
        m: {
            priority: 60,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "m":
                        return Nm(Em, e);
                    case "mo":
                        return r.ordinalNumber(e, {
                            unit: "minute"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 59
            },
            set: function(e, t, r, a) {
                return e.setUTCMinutes(r, 0, 0), e
            },
            incompatibleTokens: ["t", "T"]
        },
        s: {
            priority: 50,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "s":
                        return Nm(Pm, e);
                    case "so":
                        return r.ordinalNumber(e, {
                            unit: "second"
                        });
                    default:
                        return Um(t.length, e)
                }
            },
            validate: function(e, t, r) {
                return t >= 0 && t <= 59
            },
            set: function(e, t, r, a) {
                return e.setUTCSeconds(r, 0), e
            },
            incompatibleTokens: ["t", "T"]
        },
        S: {
            priority: 30,
            parse: function(e, t, r, a) {
                return Um(t.length, e, (function(e) {
                    return Math.floor(e * Math.pow(10, 3 - t.length))
                }))
            },
            set: function(e, t, r, a) {
                return e.setUTCMilliseconds(r), e
            },
            incompatibleTokens: ["t", "T"]
        },
        X: {
            priority: 10,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "X":
                        return Im(Fm, e);
                    case "XX":
                        return Im($m, e);
                    case "XXXX":
                        return Im(Am, e);
                    case "XXXXX":
                        return Im(Lm, e);
                    case "XXX":
                    default:
                        return Im(Mm, e)
                }
            },
            set: function(e, t, r, a) {
                return t.timestampIsSet ? e : new Date(e.getTime() - r)
            },
            incompatibleTokens: ["t", "T", "x"]
        },
        x: {
            priority: 10,
            parse: function(e, t, r, a) {
                switch (t) {
                    case "x":
                        return Im(Fm, e);
                    case "xx":
                        return Im($m, e);
                    case "xxxx":
                        return Im(Am, e);
                    case "xxxxx":
                        return Im(Lm, e);
                    case "xxx":
                    default:
                        return Im(Mm, e)
                }
            },
            set: function(e, t, r, a) {
                return t.timestampIsSet ? e : new Date(e.getTime() - r)
            },
            incompatibleTokens: ["t", "T", "X"]
        },
        t: {
            priority: 40,
            parse: function(e, t, r, a) {
                return jm(e)
            },
            set: function(e, t, r, a) {
                return [new Date(1e3 * r), {
                    timestampIsSet: !0
                }]
            },
            incompatibleTokens: "*"
        },
        T: {
            priority: 20,
            parse: function(e, t, r, a) {
                return jm(e)
            },
            set: function(e, t, r, a) {
                return [new Date(r), {
                    timestampIsSet: !0
                }]
            },
            incompatibleTokens: "*"
        }
    },
    Xm = /[yYQqMLwIdDecihHKkms]o|(\w)\1*|''|'(''|[^'])+('|$)|./g,
    Qm = /P+p+|P+|p+|''|'(''|[^'])+('|$)|./g,
    Gm = /^'([^]*?)'?$/,
    Km = /''/g,
    Jm = /\S/,
    Zm = /[a-zA-Z]/;

function ev(e, t) {
    if (t.timestampIsSet) return e;
    var r = new Date(0);
    return r.setFullYear(e.getUTCFullYear(), e.getUTCMonth(), e.getUTCDate()), r.setHours(e.getUTCHours(), e.getUTCMinutes(), e.getUTCSeconds(), e.getUTCMilliseconds()), r
}

function tv(e) {
    return e.match(Gm)[1].replace(Km, "'")
}

function rv(e, t) {
    rf(2, arguments);
    var r = af(e),
        a = af(t);
    return r.getFullYear() === a.getFullYear() && r.getMonth() === a.getMonth()
}

function av(e, t) {
    rf(2, arguments);
    var r = af(e),
        a = af(t);
    return r.getFullYear() === a.getFullYear()
}

function nv(e, t) {
    rf(2, arguments);
    var r = t || {},
        a = af(e).getTime(),
        n = af(r.start).getTime(),
        o = af(r.end).getTime();
    if (!(n <= o)) throw new RangeError("Invalid interval");
    return a >= n && a <= o
}
var ov = /(\w)\1*|''|'(''|[^'])+('|$)|./g,
    iv = /^'([^]*?)'?$/,
    sv = /''/g,
    lv = /[a-zA-Z]/;

function cv(e) {
    return e.match(iv)[1].replace(sv, "'")
}

function uv(e, t) {
    rf(2, arguments);
    var r = tf(t);
    return hf(e, -r)
}
var dv = function e(t, r, a) {
        return (a = a || []).length >= r ? t.apply(null, a.slice(0, r).reverse()) : function() {
            var n = Array.prototype.slice.call(arguments);
            return e(t, r, a.concat(n))
        }
    }((function(e, t, r) {
        rf(2, arguments);
        var a = String(t),
            n = r || {},
            o = n.locale || Sf,
            i = o.options && o.options.firstWeekContainsDate,
            s = null == i ? 1 : tf(i),
            l = null == n.firstWeekContainsDate ? s : tf(n.firstWeekContainsDate);
        if (!(l >= 1 && l <= 7)) throw new RangeError("firstWeekContainsDate must be between 1 and 7 inclusively");
        var c = o.options && o.options.weekStartsOn,
            u = null == c ? 0 : tf(c),
            d = null == n.weekStartsOn ? u : tf(n.weekStartsOn);
        if (!(d >= 0 && d <= 6)) throw new RangeError("weekStartsOn must be between 0 and 6 inclusively");
        if (!o.localize) throw new RangeError("locale must contain localize property");
        if (!o.formatLong) throw new RangeError("locale must contain formatLong property");
        var h = af(e);
        if (!pf(h)) throw new RangeError("Invalid time value");
        var p = uf(h),
            f = Cf(h, p),
            m = {
                firstWeekContainsDate: l,
                weekStartsOn: d,
                locale: o,
                _originalDate: h
            },
            v = a.match(rm).map((function(e) {
                var t = e[0];
                return "p" === t || "P" === t ? (0, Qf[t])(e, o.formatLong, m) : e
            })).join("").match(tm).map((function(r) {
                if ("''" === r) return "'";
                var a = r[0];
                if ("'" === a) return im(r);
                var i = Yf[a];
                if (i) return !n.useAdditionalWeekYearTokens && Zf(r) && em(r, t, e), !n.useAdditionalDayOfYearTokens && Jf(r) && em(r, t, e), i(f, r, o.localize, m);
                if (a.match(om)) throw new RangeError("Format string contains an unescaped latin alphabet character `" + a + "`");
                return r
            })).join("");
        return v
    }), 3),
    hv = Yr({
        emits: {
            elementClick: e => pf(e),
            left: () => !0,
            right: () => !0,
            heading: () => !0
        },
        props: {
            headingClickable: {
                type: Boolean,
                default: !1
            },
            leftDisabled: {
                type: Boolean,
                default: !1
            },
            rightDisabled: {
                type: Boolean,
                default: !1
            },
            columnCount: {
                type: Number,
                default: 7
            },
            items: {
                type: Array,
                default: () => []
            }
        }
    });
const pv = Kt("data-v-2e128338");
Qt("data-v-2e128338");
const fv = {
        class: "v3dp__heading"
    },
    mv = wa("svg", {
        class: "v3dp__heading__icon",
        xmlns: "http://www.w3.org/2000/svg",
        viewBox: "0 0 6 8"
    }, [wa("g", {
        fill: "none",
        "fill-rule": "evenodd"
    }, [wa("path", {
        stroke: "none",
        d: "M-9 16V-8h24v24z"
    }), wa("path", {
        "stroke-linecap": "round",
        "stroke-linejoin": "round",
        d: "M5 0L1 4l4 4"
    })])], -1),
    vv = wa("svg", {
        class: "v3dp__heading__icon",
        xmlns: "http://www.w3.org/2000/svg",
        viewBox: "0 0 6 8"
    }, [wa("g", {
        fill: "none",
        "fill-rule": "evenodd"
    }, [wa("path", {
        stroke: "none",
        d: "M15-8v24H-9V-8z"
    }), wa("path", {
        "stroke-linecap": "round",
        "stroke-linejoin": "round",
        d: "M1 8l4-4-4-4"
    })])], -1),
    gv = {
        class: "v3dp__body"
    },
    yv = {
        class: "v3dp__subheading"
    },
    bv = wa("hr", {
        class: "v3dp__divider"
    }, null, -1),
    wv = {
        class: "v3dp__elements"
    };
Gt();
const Ev = pv((function(e, t, r, a, n, o) {
    return ha(), fa("div", {
        class: "v3dp__popout",
        style: {
            "--popout-column-definition": `repeat(${e.columnCount}, 1fr)`
        },
        onMousedown: t[4] || (t[4] = Hn((() => {}), ["prevent"]))
    }, [wa("div", fv, [wa("button", {
        class: "v3dp__heading__button",
        disabled: e.leftDisabled,
        onClick: t[1] || (t[1] = Hn((t => e.$emit("left")), ["stop", "prevent"]))
    }, [Bt(e.$slots, "arrow-left", {}, (() => [mv]))], 8, ["disabled"]), (ha(), fa(aa(e.headingClickable ? "button" : "span"), {
        class: "v3dp__heading__center",
        onClick: t[2] || (t[2] = Hn((t => e.$emit("heading")), ["stop", "prevent"]))
    }, {
        default: pv((() => [Bt(e.$slots, "heading")])),
        _: 3
    })), wa("button", {
        class: "v3dp__heading__button",
        disabled: e.rightDisabled,
        onClick: t[3] || (t[3] = Hn((t => e.$emit("right")), ["stop", "prevent"]))
    }, [Bt(e.$slots, "arrow-right", {}, (() => [vv]))], 8, ["disabled"])]), wa("div", gv, ["subheading" in e.$slots ? (ha(), fa(ia, {
        key: 0
    }, [wa("div", yv, [Bt(e.$slots, "subheading")]), bv], 64)) : _a("v-if", !0), wa("div", wv, [Bt(e.$slots, "body", {}, (() => [(ha(!0), fa(ia, null, en(e.items, (t => (ha(), fa("button", {
        key: t.key,
        disabled: t.disabled,
        class: {
            selected: t.selected
        },
        onClick: Hn((r => e.$emit("elementClick", t.value)), ["stop", "prevent"])
    }, [wa("span", null, u(t.display), 1)], 10, ["disabled", "onClick"])))), 128))]))])])], 36)
}));
hv.render = Ev, hv.__scopeId = "data-v-2e128338", hv.__file = "src/datepicker/PickerPopup.vue";
var Pv = Yr({
    components: {
        PickerPopup: hv
    },
    emits: {
        "update:pageDate": e => pf(e),
        select: e => pf(e)
    },
    props: {
        selected: {
            type: Date,
            required: !1
        },
        pageDate: {
            type: Date,
            required: !0
        },
        lowerLimit: {
            type: Date,
            required: !1
        },
        upperLimit: {
            type: Date,
            required: !1
        }
    },
    setup(e, {
        emit: t
    }) {
        const r = Ja((() => function(e) {
                rf(1, arguments);
                var t = af(e),
                    r = t.getFullYear(),
                    a = 10 * Math.floor(r / 10);
                return t.setFullYear(a, 0, 1), t.setHours(0, 0, 0, 0), t
            }(e.pageDate))),
            a = Ja((() => function(e) {
                rf(1, arguments);
                var t = af(e),
                    r = t.getFullYear(),
                    a = 9 + 10 * Math.floor(r / 10);
                return t.setFullYear(a, 11, 31), t.setHours(23, 59, 59, 999), t
            }(e.pageDate)));
        return {
            years: Ja((() => function(e) {
                rf(1, arguments);
                var t = e || {},
                    r = af(t.start),
                    a = af(t.end).getTime();
                if (!(r.getTime() <= a)) throw new RangeError("Invalid interval");
                var n = [],
                    o = r;
                for (o.setHours(0, 0, 0, 0), o.setMonth(0, 1); o.getTime() <= a;) n.push(af(o)), o.setFullYear(o.getFullYear() + 1);
                return n
            }({
                start: r.value,
                end: a.value
            }).map((t => {
                return {
                    value: t,
                    key: String(cm(t)),
                    display: cm(t),
                    selected: e.selected && cm(t) === cm(e.selected),
                    disabled: (r = t, a = e.lowerLimit, n = e.upperLimit, !!((a || n) && (a && cm(r) < cm(a) || n && cm(r) > cm(n))))
                };
                var r, a, n
            })))),
            heading: Ja((() => `${cm(r.value)} - ${cm(a.value)}`)),
            leftDisabled: Ja((() => e.lowerLimit && (lm(e.lowerLimit) === lm(e.pageDate) || dm(e.pageDate, e.lowerLimit)))),
            rightDisabled: Ja((() => e.upperLimit && (lm(e.upperLimit) === lm(e.pageDate) || um(e.pageDate, e.upperLimit)))),
            previousPage: () => t("update:pageDate", uv(e.pageDate, 10)),
            nextPage: () => t("update:pageDate", hf(e.pageDate, 10))
        }
    }
});
Pv.render = function(e, t, r, a, n, o) {
    const i = ta("picker-popup");
    return ha(), fa(i, {
        columnCount: 3,
        leftDisabled: e.leftDisabled,
        rightDisabled: e.rightDisabled,
        items: e.years,
        onLeft: e.previousPage,
        onRight: e.nextPage,
        onElementClick: t[1] || (t[1] = t => e.$emit("select", t))
    }, {
        heading: Vt((() => [Pa(u(e.heading), 1)])),
        _: 1
    }, 8, ["leftDisabled", "rightDisabled", "items", "onLeft", "onRight"])
}, Pv.__file = "src/datepicker/YearPicker.vue";
var kv = Yr({
    components: {
        PickerPopup: hv
    },
    emits: {
        "update:pageDate": e => pf(e),
        select: e => pf(e),
        back: () => !0
    },
    props: {
        selected: {
            type: Date,
            required: !1
        },
        pageDate: {
            type: Date,
            required: !0
        },
        format: {
            type: String,
            required: !1,
            default: "LLL"
        },
        locale: {
            type: Object,
            required: !1
        },
        lowerLimit: {
            type: Date,
            required: !1
        },
        upperLimit: {
            type: Date,
            required: !1
        }
    },
    setup(e, {
        emit: t
    }) {
        const r = Ja((() => function(e) {
                rf(1, arguments);
                var t = af(e),
                    r = new Date(0);
                return r.setFullYear(t.getFullYear(), 0, 1), r.setHours(0, 0, 0, 0), r
            }(e.pageDate))),
            a = Ja((() => function(e) {
                rf(1, arguments);
                var t = af(e),
                    r = t.getFullYear();
                return t.setFullYear(r + 1, 0, 0), t.setHours(23, 59, 59, 999), t
            }(e.pageDate))),
            n = Ja((() => dv({
                locale: e.locale
            })(e.format)));
        return {
            months: Ja((() => function(e) {
                rf(1, arguments);
                var t = e || {},
                    r = af(t.start),
                    a = af(t.end).getTime();
                if (!(r.getTime() <= a)) throw new RangeError("Invalid interval");
                var n = [],
                    o = r;
                for (o.setHours(0, 0, 0, 0), o.setDate(1); o.getTime() <= a;) n.push(af(o)), o.setMonth(o.getMonth() + 1);
                return n
            }({
                start: r.value,
                end: a.value
            }).map((t => {
                return {
                    value: t,
                    display: n.value(t),
                    key: n.value(t),
                    selected: e.selected && rv(e.selected, t),
                    disabled: (r = t, a = e.lowerLimit, o = e.upperLimit, !!((a || o) && (a && dm(r, mf(a)) || o && um(r, vf(o)))))
                };
                var r, a, o
            })))),
            heading: Ja((() => cm(r.value))),
            leftDisabled: Ja((() => e.lowerLimit && (av(e.lowerLimit, e.pageDate) || dm(e.pageDate, e.lowerLimit)))),
            rightDisabled: Ja((() => e.upperLimit && (av(e.upperLimit, e.pageDate) || um(e.pageDate, e.upperLimit)))),
            previousPage: () => t("update:pageDate", uv(e.pageDate, 1)),
            nextPage: () => t("update:pageDate", hf(e.pageDate, 1))
        }
    }
});
kv.render = function(e, t, r, a, n, o) {
    const i = ta("picker-popup");
    return ha(), fa(i, {
        headingClickable: "",
        columnCount: 3,
        items: e.months,
        leftDisabled: e.leftDisabled,
        rightDisabled: e.rightDisabled,
        onLeft: e.previousPage,
        onRight: e.nextPage,
        onHeading: t[1] || (t[1] = t => e.$emit("back")),
        onElementClick: t[2] || (t[2] = t => e.$emit("select", t))
    }, {
        heading: Vt((() => [Pa(u(e.heading), 1)])),
        _: 1
    }, 8, ["items", "leftDisabled", "rightDisabled", "onLeft", "onRight"])
}, kv.__file = "src/datepicker/MonthPicker.vue";
var _v = Yr({
    components: {
        PickerPopup: hv
    },
    emits: {
        "update:pageDate": e => pf(e),
        select: e => pf(e),
        back: () => !0
    },
    props: {
        selected: {
            type: Date,
            required: !1
        },
        pageDate: {
            type: Date,
            required: !0
        },
        format: {
            type: String,
            required: !1,
            default: "dd"
        },
        headingFormat: {
            type: String,
            required: !1,
            default: "LLLL yyyy"
        },
        weekdayFormat: {
            type: String,
            required: !1,
            default: "EE"
        },
        locale: {
            type: Object,
            required: !1
        },
        weekStartsOn: {
            type: Number,
            required: !1,
            default: 1,
            validator: e => "number" == typeof e && Number.isInteger(e) && e >= 0 && e <= 6
        },
        lowerLimit: {
            type: Date,
            required: !1
        },
        upperLimit: {
            type: Date,
            required: !1
        }
    },
    setup(e, {
        emit: t
    }) {
        const r = Ja((() => dv({
                locale: e.locale,
                weekStartsOn: e.weekStartsOn
            }))),
            a = Ja((() => mf(e.pageDate))),
            n = Ja((() => vf(e.pageDate))),
            o = Ja((() => ({
                start: a.value,
                end: n.value
            }))),
            i = Ja((() => ({
                start: lf(a.value, {
                    weekStartsOn: e.weekStartsOn
                }),
                end: gf(n.value, {
                    weekStartsOn: e.weekStartsOn
                })
            }))),
            s = Ja((() => {
                const t = e.weekStartsOn,
                    a = r.value(e.weekdayFormat);
                return Array.from(Array(7)).map(((e, r) => (t + r) % 7)).map((t => function(e, t, r) {
                    rf(2, arguments);
                    var a = r || {},
                        n = a.locale,
                        o = n && n.options && n.options.weekStartsOn,
                        i = null == o ? 0 : tf(o),
                        s = null == a.weekStartsOn ? i : tf(a.weekStartsOn);
                    if (!(s >= 0 && s <= 6)) throw new RangeError("weekStartsOn must be between 0 and 6 inclusively");
                    var l = af(e, a),
                        c = tf(t),
                        u = l.getDay(),
                        d = (c % 7 + 7) % 7,
                        h = 7 - s;
                    return nf(l, c < 0 || c > 6 ? c - (u + h) % 7 : (d + h) % 7 - (u + h) % 7, a)
                }(new Date, t, {
                    weekStartsOn: e.weekStartsOn
                }))).map(a)
            })),
            l = (e, t, r) => !t && !r || (!t || !dm(e, df(t))) && (!r || !um(e, function(e) {
                rf(1, arguments);
                var t = af(e);
                return t.setHours(23, 59, 59, 999), t
            }(r)));
        return {
            weekDays: s,
            days: Ja((() => {
                const t = r.value(e.format);
                return function(e, t) {
                    rf(1, arguments);
                    var r = e || {},
                        a = af(r.start),
                        n = af(r.end).getTime();
                    if (!(a.getTime() <= n)) throw new RangeError("Invalid interval");
                    var o = [],
                        i = a;
                    i.setHours(0, 0, 0, 0);
                    var s = t && "step" in t ? Number(t.step) : 1;
                    if (s < 1 || isNaN(s)) throw new RangeError("`options.step` must be a number greater than 1");
                    for (; i.getTime() <= n;) o.push(af(i)), i.setDate(i.getDate() + s), i.setHours(0, 0, 0, 0);
                    return o
                }(i.value).map((a => ({
                    value: a,
                    display: t(a),
                    selected: e.selected && ff(e.selected, a),
                    disabled: !nv(a, o.value) || !l(a, e.lowerLimit, e.upperLimit),
                    key: r.value("yyyy-MM-dd", a)
                })))
            })),
            heading: Ja((() => r.value(e.headingFormat)(e.pageDate))),
            leftDisabled: Ja((() => e.lowerLimit && (rv(e.lowerLimit, e.pageDate) || dm(e.pageDate, e.lowerLimit)))),
            rightDisabled: Ja((() => e.upperLimit && (rv(e.upperLimit, e.pageDate) || um(e.pageDate, e.upperLimit)))),
            previousPage: () => t("update:pageDate", function(e, t) {
                rf(2, arguments);
                var r = tf(t);
                return of(e, -r)
            }(e.pageDate, 1)),
            nextPage: () => t("update:pageDate", of (e.pageDate, 1))
        }
    }
});
_v.render = function(e, t, r, a, n, o) {
    const i = ta("picker-popup");
    return ha(), fa(i, {
        headingClickable: "",
        leftDisabled: e.leftDisabled,
        rightDisabled: e.rightDisabled,
        items: e.days,
        onLeft: e.previousPage,
        onRight: e.nextPage,
        onHeading: t[1] || (t[1] = t => e.$emit("back")),
        onElementClick: t[2] || (t[2] = t => e.$emit("select", t))
    }, {
        heading: Vt((() => [Pa(u(e.heading), 1)])),
        subheading: Vt((() => [(ha(!0), fa(ia, null, en(e.weekDays, (e => (ha(), fa("span", {
            key: e
        }, u(e), 1)))), 128))])),
        _: 1
    }, 8, ["leftDisabled", "rightDisabled", "items", "onLeft", "onRight"])
}, _v.__file = "src/datepicker/DayPicker.vue";
var Sv = Yr({
    components: {
        YearPicker: Pv,
        MonthPicker: kv,
        DayPicker: _v
    },
    props: {
        placeholder: {
            type: String,
            default: ""
        },
        modelValue: {
            type: Date,
            required: !1
        },
        upperLimit: {
            type: Date,
            required: !1
        },
        lowerLimit: {
            type: Date,
            required: !1
        },
        startingView: {
            type: String,
            required: !1,
            default: "day",
            validate: e => "string" == typeof e && ["day", "month", "year"].includes(e)
        },
        monthHeadingFormat: {
            type: String,
            required: !1,
            default: "LLLL yyyy"
        },
        monthListFormat: {
            type: String,
            required: !1,
            default: "LLL"
        },
        weekdayFormat: {
            type: String,
            required: !1,
            default: "EE"
        },
        inputFormat: {
            type: String,
            required: !1,
            default: "yyyy-MM-dd"
        },
        locale: {
            type: Object,
            required: !1
        },
        weekStartsOn: {
            type: Number,
            required: !1,
            default: 1,
            validator: e => [0, 1, 2, 3, 4, 5, 6].includes(e)
        },
        disabled: {
            type: Boolean,
            required: !1,
            default: !1
        }
    },
    setup(e, {
        emit: t
    }) {
        const r = Ze("none"),
            a = Ze(new Date),
            n = Ze("");
        vr((() => {
            const t = function(e, t, r, a) {
                rf(3, arguments);
                var n = String(e),
                    o = String(t),
                    i = a || {},
                    s = i.locale || Sf;
                if (!s.match) throw new RangeError("locale must contain match property");
                var l = s.options && s.options.firstWeekContainsDate,
                    c = null == l ? 1 : tf(l),
                    u = null == i.firstWeekContainsDate ? c : tf(i.firstWeekContainsDate);
                if (!(u >= 1 && u <= 7)) throw new RangeError("firstWeekContainsDate must be between 1 and 7 inclusively");
                var d = s.options && s.options.weekStartsOn,
                    h = null == d ? 0 : tf(d),
                    p = null == i.weekStartsOn ? h : tf(i.weekStartsOn);
                if (!(p >= 0 && p <= 6)) throw new RangeError("weekStartsOn must be between 0 and 6 inclusively");
                if ("" === o) return "" === n ? af(r) : new Date(NaN);
                var f, m = {
                        firstWeekContainsDate: u,
                        weekStartsOn: p,
                        locale: s
                    },
                    v = [{
                        priority: 10,
                        subPriority: -1,
                        set: ev,
                        index: 0
                    }],
                    g = o.match(Qm).map((function(e) {
                        var t = e[0];
                        return "p" === t || "P" === t ? (0, Qf[t])(e, s.formatLong, m) : e
                    })).join("").match(Xm),
                    y = [];
                for (f = 0; f < g.length; f++) {
                    var b = g[f];
                    !i.useAdditionalWeekYearTokens && Zf(b) && em(b, o, e), !i.useAdditionalDayOfYearTokens && Jf(b) && em(b, o, e);
                    var w = b[0],
                        E = zm[w];
                    if (E) {
                        var P = E.incompatibleTokens;
                        if (Array.isArray(P)) {
                            for (var k = void 0, _ = 0; _ < y.length; _++) {
                                var S = y[_].token;
                                if (-1 !== P.indexOf(S) || S === w) {
                                    k = y[_];
                                    break
                                }
                            }
                            if (k) throw new RangeError("The format string mustn't contain `".concat(k.fullToken, "` and `").concat(b, "` at the same time"))
                        } else if ("*" === E.incompatibleTokens && y.length) throw new RangeError("The format string mustn't contain `".concat(b, "` and any other token at the same time"));
                        y.push({
                            token: w,
                            fullToken: b
                        });
                        var C = E.parse(n, b, s.match, m);
                        if (!C) return new Date(NaN);
                        v.push({
                            priority: E.priority,
                            subPriority: E.subPriority || 0,
                            set: E.set,
                            validate: E.validate,
                            value: C.value,
                            index: v.length
                        }), n = C.rest
                    } else {
                        if (w.match(Zm)) throw new RangeError("Format string contains an unescaped latin alphabet character `" + w + "`");
                        if ("''" === b ? b = "'" : "'" === w && (b = tv(b)), 0 !== n.indexOf(b)) return new Date(NaN);
                        n = n.slice(b.length)
                    }
                }
                if (n.length > 0 && Jm.test(n)) return new Date(NaN);
                var T = v.map((function(e) {
                        return e.priority
                    })).sort((function(e, t) {
                        return t - e
                    })).filter((function(e, t, r) {
                        return r.indexOf(e) === t
                    })).map((function(e) {
                        return v.filter((function(t) {
                            return t.priority === e
                        })).sort((function(e, t) {
                            return t.subPriority - e.subPriority
                        }))
                    })).map((function(e) {
                        return e[0]
                    })),
                    x = af(r);
                if (isNaN(x)) return new Date(NaN);
                var D = Cf(x, uf(x)),
                    O = {};
                for (f = 0; f < T.length; f++) {
                    var R = T[f];
                    if (R.validate && !R.validate(D, R.value, m)) return new Date(NaN);
                    var F = R.set(D, O, R.value, m);
                    F[0] ? (D = F[0], sm(O, F[1])) : D = F
                }
                return D
            }(n.value, e.inputFormat, new Date);
            pf(t) && (a.value = t)
        })), vr((() => n.value = e.modelValue && pf(e.modelValue) ? function(e, t) {
            rf(2, arguments);
            var r = String(t),
                a = af(e);
            if (!pf(a)) throw new RangeError("Invalid time value");
            var n = uf(a),
                o = Cf(a, n);
            return r.match(ov).map((function(e) {
                if ("''" === e) return "'";
                var t = e[0];
                if ("'" === t) return cv(e);
                var r = xf[t];
                if (r) return r(o, e, null, {});
                if (t.match(lv)) throw new RangeError("Format string contains an unescaped latin alphabet character `" + t + "`");
                return e
            })).join("")
        }(e.modelValue, e.inputFormat) : ""));
        vr((() => {
            e.disabled && (r.value = "none")
        }));
        return {
            input: n,
            pageDate: a,
            renderView: (t = "none") => {
                e.disabled || (r.value = t)
            },
            selectYear: e => {
                a.value = e, r.value = "month"
            },
            selectMonth: e => {
                a.value = e, r.value = "day"
            },
            selectDay: e => {
                t("update:modelValue", e), r.value = "none"
            },
            viewShown: r,
            log: e => console.log(e)
        }
    }
});
const Cv = {
    class: "v3dp__datepicker"
};
Sv.render = function(e, t, r, a, n, o) {
    const i = ta("year-picker"),
        s = ta("month-picker"),
        l = ta("day-picker");
    return ha(), fa("div", Cv, [Ir(wa("input", {
        type: "text",
        readonly: "readonly",
        "onUpdate:modelValue": t[1] || (t[1] = t => e.input = t),
        placeholder: e.placeholder,
        disabled: e.disabled,
        tabindex: e.disabled ? -1 : 0,
        onBlur: t[2] || (t[2] = t => e.renderView()),
        onFocus: t[3] || (t[3] = t => e.renderView(e.startingView)),
        onClick: t[4] || (t[4] = t => e.renderView(e.startingView))
    }, null, 40, ["placeholder", "disabled", "tabindex"]), [
        [Mn, e.input]
    ]), Ir(wa(i, {
        pageDate: e.pageDate,
        "onUpdate:pageDate": t[5] || (t[5] = t => e.pageDate = t),
        selected: e.modelValue,
        lowerLimit: e.lowerLimit,
        upperLimit: e.upperLimit,
        onSelect: e.selectYear
    }, null, 8, ["pageDate", "selected", "lowerLimit", "upperLimit", "onSelect"]), [
        [Bn, "year" === e.viewShown]
    ]), Ir(wa(s, {
        pageDate: e.pageDate,
        "onUpdate:pageDate": t[6] || (t[6] = t => e.pageDate = t),
        selected: e.modelValue,
        onSelect: e.selectMonth,
        lowerLimit: e.lowerLimit,
        upperLimit: e.upperLimit,
        format: e.monthListFormat,
        headingFormat: e.monthHeadingFormat,
        locale: e.locale,
        onBack: t[7] || (t[7] = t => e.viewShown = "year")
    }, null, 8, ["pageDate", "selected", "onSelect", "lowerLimit", "upperLimit", "format", "headingFormat", "locale"]), [
        [Bn, "month" === e.viewShown]
    ]), Ir(wa(l, {
        pageDate: e.pageDate,
        "onUpdate:pageDate": t[8] || (t[8] = t => e.pageDate = t),
        selected: e.modelValue,
        weekStartsOn: e.weekStartsOn,
        lowerLimit: e.lowerLimit,
        upperLimit: e.upperLimit,
        locale: e.locale,
        weekdayFormat: e.weekdayFormat,
        onSelect: e.selectDay,
        onBack: t[9] || (t[9] = t => e.viewShown = "month")
    }, null, 8, ["pageDate", "selected", "weekStartsOn", "lowerLimit", "upperLimit", "locale", "weekdayFormat", "onSelect"]), [
        [Bn, "day" === e.viewShown]
    ])])
}, Sv.__file = "src/datepicker/Datepicker.vue";
var Tv = {
    props: {
        name: String,
        readonly: {
            type: String,
            default: null
        },
        disabled: {
            type: Boolean,
            default: null
        },
        validator: {
            type: Object,
            default: null
        }
    },
    watch: {
        picker(e) {
            this.edited = !0, this.name && this.validator && (this.validator.set(this.name, ru(e).format("YYYY-MM-DD")), this.validator.validate(), this.checkErrors())
        }
    },
    data: () => ({
        upperLimit: new Date,
        picker: null,
        errors: !1,
        edited: !1
    }),
    computed: {
        error() {
            return !(!this.errors || !this.errors[0]) && this.errors[0].keyword
        },
        isEdited() {
            return this.checkErrors(), this.edited || this.validator?.force_validate
        },
        style() {
            return !!this.isEdited && (this.errors ? "error" : "validated")
        }
    },
    methods: {
        checkErrors() {
            this.validator && (this.errors = this.validator.getErrors(this.name))
        },
        parseValue(e) {
            return "number" === this.type ? "" === e ? null : Number(e) : e
        },
        handleIconClick(e) {
            this.$emit("iconClick", e)
        }
    },
    components: {
        Datepicker: Sv
    }
};
const xv = {
        key: 0,
        class: "error-text"
    },
    Dv = {
        class: "input"
    };
Tv.render = function(e, t, r, a, n, o) {
    const i = ta("Datepicker");
    return ha(), fa("div", {
        class: ["input-wrapper", o.style]
    }, [o.isEdited && n.errors ? (ha(), fa("span", xv, u(o.error), 1)) : _a("", !0), wa("div", Dv, [wa(i, {
        name: r.name,
        modelValue: n.picker,
        "onUpdate:modelValue": t[1] || (t[1] = e => n.picker = e),
        disabled: r.disabled,
        readonly: r.readonly,
        inputFormat: "dd/MM/yyyy",
        upperLimit: n.upperLimit
    }, null, 8, ["name", "modelValue", "disabled", "readonly", "upperLimit"])])], 2)
};
var Ov = {
    setup() {
        const {
            addNotify: e
        } = bc;
        return {
            addNotify: e
        }
    },
    data: () => ({
        disabled: !1,
        ban: null,
        show_profile: !1,
        profile: null,
        OffenseEnum: Kc,
        PaymentMethodEnum: zc,
        TradeTypeEnum: Qc,
        submitted: !1,
        validator: new nc("feedback", "reportUser", {
            from_steam_id: mc.data.session && mc.data.session.steam_id
        })
    }),
    methods: {
        getAvatarPath: gc,
        async handleSubmit() {
            try {
                if (this.disabled) return void this.addNotify({
                    title: "Cooldown...",
                    type: "warning"
                });
                this.disabled = !0;
                const e = this.validator.data.to_steam_id,
                    t = this.validator.validate();
                this.validator.force();
                let r = null;
                t && (!this.profile || this.profile && this.profile.steam_id !== mc.data.session.steam_id) && (r = await uc("feedback", "reportUser", this.validator.data)), t && r ? (this.addNotify({
                    title: "Form accepted!",
                    content: "Your form was submitted successfully!",
                    type: "success"
                }), await this.$router.push(`/profile/${e}`)) : this.addNotify({
                    title: "Fix the form",
                    type: "error"
                })
            } catch (e) {
                2001 === e.error && this.addNotify({
                    title: "Cooldown...",
                    type: "warning"
                })
            } finally {
                setTimeout((() => {
                    this.disabled = !1
                }), 5e3)
            }
        },
        async handleProfileSearch() {
            const e = this.validator.data.to_steam_id;
            if (!e || this.validator.getErrors("to_steam_id") || this.profile?.steam_id === e) return;
            this.ban = !1, this.show_profile = !1, this.profile = !1;
            const {
                profile: t,
                ban: r
            } = await uc("feedback", "searchUser", {
                steam_id: e
            });
            t?.steam_id !== mc.data.session.steam_id ? (this.ban = r, this.profile = t, this.show_profile = !0) : this.addNotify({
                title: "Wrong profile",
                content: "You cannot report yourself",
                type: "error"
            })
        },
        handlePaste(e) {
            e.preventDefault();
            const t = e.clipboardData.getData("Text").replace(/\D/gi, "");
            return t.length > 0 && (this.validator.set("to_steam_id", t), this.validator.validate()), !1
        }
    },
    components: {
        Datepick: Tv,
        ButtonGroup: lu,
        Input: qc,
        Message: nu,
        Footer: Md
    }
};
const Rv = {
        id: "subpage-report_user",
        class: "subpage"
    },
    Fv = wa("div", {
        class: "page-heading"
    }, [wa("div", {
        class: "wrapper"
    }, [wa("div", {
        class: "heading"
    }, "Report user")])], -1),
    $v = {
        class: "details"
    },
    Av = {
        class: "user-link"
    },
    Mv = wa("div", {
        class: "title"
    }, "Write SteamID64 or Steam profile link here:", -1),
    Lv = {
        key: 0,
        class: "user-result"
    },
    Nv = {
        key: 0,
        class: "user-not-"
    },
    Iv = {
        key: 1,
        class: "user-not-"
    },
    jv = {
        key: 2,
        class: "user-preview"
    },
    Uv = {
        class: "avatar"
    },
    Hv = {
        class: "user-id"
    },
    qv = wa("div", {
        class: "title"
    }, "Victim's ID64:", -1),
    Yv = {
        class: "date"
    },
    Bv = wa("div", {
        class: "title"
    }, "Date:", -1),
    Wv = {
        class: "message"
    },
    Vv = wa("div", {
        class: "title"
    }, "Description:", -1),
    zv = {
        class: "links"
    },
    Xv = wa("div", {
        class: "title"
    }, "Proof link (optional):", -1),
    Qv = {
        class: "details-select"
    },
    Gv = {
        class: "select-wrapper"
    },
    Kv = {
        class: "send-report"
    },
    Jv = wa("span", {
        class: "text"
    }, "Send report", -1),
    Zv = wa("span", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/send.svg"
    })], -1),
    eg = {
        key: 1,
        class: "submitted"
    },
    tg = wa("div", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/successful.svg"
    }), wa("div", {
        class: "title"
    }, "Thank you!")], -1),
    rg = wa("div", {
        class: "content"
    }, " The form was submitted successfully. ", -1);
Ov.render = function(e, t, r, a, n, o) {
    const i = ta("Input"),
        s = ta("Datepick"),
        l = ta("Message"),
        c = ta("ButtonGroup"),
        u = ta("Footer");
    return ha(), fa("div", Rv, [Fv, n.submitted ? (ha(), fa("div", eg, [tg, rg])) : (ha(), fa("div", {
        key: 0,
        class: "content-wrapper",
        onKeyup: t[2] || (t[2] = Yn(((...e) => o.handleSubmit && o.handleSubmit(...e)), ["enter"]))
    }, [wa("div", $v, [wa("div", Av, [Mv, wa(i, {
        name: "to_steam_id",
        placeholder: "765...",
        onPaste: o.handlePaste,
        onBlur: o.handleProfileSearch,
        validator: n.validator
    }, null, 8, ["onPaste", "onBlur", "validator"])]), n.show_profile ? (ha(), fa("div", Lv, [n.ban ? (ha(), fa("div", Nv, " This user is banned ")) : n.profile ? (ha(), fa("div", jv, [wa("div", Uv, [wa("img", {
        src: o.getAvatarPath(n.profile.avatar)
    }, null, 8, ["src"])]), wa("div", {
        class: "nickname",
        innerHTML: n.profile.username
    }, null, 8, ["innerHTML"])])) : (ha(), fa("div", Iv, " Profile not found :( "))])) : _a("", !0), wa("div", Hv, [qv, wa(i, {
        name: "from_steam_id",
        readonly: "true",
        validator: n.validator
    }, null, 8, ["validator"])]), wa("div", Yv, [Bv, wa(s, {
        name: "scammed_at",
        validator: n.validator
    }, null, 8, ["validator"])]), wa("div", Wv, [Vv, wa(l, {
        name: "body",
        validator: n.validator
    }, null, 8, ["validator"])]), wa("div", zv, [Xv, wa(i, {
        name: "proof[0]",
        placeholder: "Proof link",
        validator: n.validator
    }, null, 8, ["validator"])])]), wa("div", Qv, [wa("div", Gv, [wa(c, {
        options: n.OffenseEnum,
        class: "offense",
        name: "offense",
        title: "Offense",
        validator: n.validator
    }, null, 8, ["options", "validator"]), wa(c, {
        options: n.TradeTypeEnum,
        class: "trade_type",
        name: "trade_type",
        title: "Trade type",
        validator: n.validator
    }, null, 8, ["options", "validator"])]), wa(c, {
        options: n.PaymentMethodEnum,
        class: "payment_method",
        name: "payment_method",
        title: "Payment method",
        validator: n.validator
    }, null, 8, ["options", "validator"])]), wa("div", Kv, [wa("button", {
        class: ["btn btn-blue hvr-bounce-to-right", {
            disabled: n.disabled || !n.validator.valid || !n.show_profile
        }],
        onClick: t[1] || (t[1] = (...e) => o.handleSubmit && o.handleSubmit(...e))
    }, [Jv, Zv], 2)])], 32)), wa(u)])
};
var ag = {
    components: {
        LoginButton: hc,
        Footer: Md
    }
};
const ng = {
        class: "subpage",
        id: "subpage-login"
    },
    og = {
        class: "login-wrapper"
    },
    ig = wa("div", {
        class: "login"
    }, "You need to log in to access this part of the site.", -1);
ag.render = function(e, t, r, a, n, o) {
    const i = ta("LoginButton"),
        s = ta("Footer");
    return ha(), fa("div", ng, [wa("div", og, [ig, wa(i)]), wa(s)])
};
var sg = {
    components: {
        Footer: Md
    }
};
const lg = {
        id: "subpage-faq",
        class: "subpage"
    },
    cg = ka('<div class="page-heading">FAQ</div><div class="faq"> <div class="faq-item faq-item-1"> <div class="title">INTRODUCTION</div> <div class="content"> <p>CSGO-Rep.com is a platform created for traders by traders. Our objective is to provide a platform where you can safely choose who you trade with, as well as provide you with a way to start your journey in this community.</p> </div> </div> <div class="faq-item faq-item-2"> <div class="title">WHAT IS A FEEDBACK?</div> <div class="content"> <p>A Feedback, also known as &quot;rep&quot; or &quot;reputation&quot;, is essentially a rating that you can write on someone&#39;s profile after you&#39;ve completed a trade with someone (and the other user can do the same for you). </p> <p>If you successfully complete a trade involving something outside of the Steam trading window (which means someone had to send something first, expecting the other user to finish the agreement), it&#39;s important to make sure to write Feedback on that user&#39;s profile so that the community can check the user&#39;s trade history in the future and it&#39;ll help everyone make a decision next time they&#39;re looking to complete a transaction.</p> </div> </div> <div class="faq-item faq-item-3"> <div class="title">WHAT DOES POSITIVE AND NEUTRAL FEEDBACK MEAN? WHY IS THERE NO NEGATIVE OPTION? </div> <div class="content"> <p>Feedback can only have one of two ratings, positive and neutral.</p> <p>Positive should be used when a trade is completed successfully without any kind of issues, both users felt completely comfortable during the whole process, the user was reasonable, no sudden unjustified change of plans and the transaction was an overall great experience.</p> <p>Neutral should be used when a trade is completed successfully, but there was an issue. This can be due to a wide variety of reasons, the trade was started and the user disappeared for days without notice, the trade is halfway done and the user decides to back down and revert everything, or any other situation that makes you feel uncomfortable and have an unpleasant experience.</p> <p>Negative feedback does not exist in CSGO-Rep. The reason for this is, if someone is worthy of a negative feedback, it means the user scammed someone, in which case a report is filed against that user and the user will be banned for that action. In other words, negative feedback is replaced by a direct ban to the user at fault. </p> </div> </div> <div class="faq-item faq-item-4"> <div class="title">HOW DO I REPORT A FAKE / SPAM FEEDBACK? </div> <div class="content"> <p>Feedback can be reported by clicking the flag icon on the bottom right side of any feedback on the site, and filling the form with the requested information.</p> </div> </div> <div class="faq-item faq-item-5"> <div class="title">IF SOMEONE HAS A LARGE AMOUNT OF POSITIVE FEEDBACK, DOES THAT MEAN HE WON&#39;T SCAM ME? </div> <div class="content"> <p>No, it does not.</p> <p>While feedback is a great way to see someone&#39;s past trades and the overall experience other users have had with a specific user, it is not a guarantee that everything will go well with your transaction.</p> <p>Feedback should only be used as a way to quickly check the trades someone has made in the past and have a general idea of the experience you can expect when trading with that user.</p> <p>However, if someone is banned for scamming, it is strongly advised not to go through with any transaction with this user, as it is very likely that something will go wrong.</p> </div> </div> <div class="faq-item faq-item-6"> <div class="title">WHAT IS MIDDLEMAN FEEDBACK?</div> <div class="content"> <p>Middleman feedback is a specific type of feedback that is given when a person that&#39;s not the seller or buyer assists in the trade by holding the item / money from one user until the other party goes through with the transaction.</p> <p>Middleman feedback should only be given to the person assisting with the trade, not to the seller or buyer.</p> </div> </div> <div class="faq-item faq-item-7"> <div class="title">CAN I WRITE FEEDBACK FOR SELLING GENUINE PINS, ARTWORK, OR SOMETHING ELSE OTHER THAN ITEMS / BALANCE?</div> <div class="content"> <p>This site is aimed at transactions directly related to the biggest games with an active and large economy on Steam. For that reason, external things such as artwork (even if it&#39;s related to the game) or other kind of services should not be the reason of a feedback.</p> <p>Genuine pins are a part of the game and for that reason it is allowed to write feedback for the transaction of Genuine pins. However, the buyer of the pin must have the pin activated on his own inventory after the trade is complete in order for the feedback to be valid. This means feedback for reselling pins should not be here.</p> </div> </div> <div class="faq-item faq-item-8"> <div class="title">WHAT KIND OF BALANCE TRANSACTION CAN I WRITE FEEDBACK ABOUT?</div> <div class="content"> <p>For the time being, Buff balance transactions are the only ones accepted.</p> <p>Transactions that involve any other site or site balance, be it a marketplace or a gambling site, will not count as a valid transaction or form of payment.</p> </div> </div> <div class="faq-item faq-item-9"> <div class="title">CAN I WRITE FEEDBACKS IN ANY LANGUAGE?</div> <div class="content"> <p>Feedbacks can only be written in English.</p> </div> </div> <div class="faq-item faq-item-10"> <div class="title">I AM BANNED, WHAT DO I DO?</div> <div class="content"> <p>If you believe you were incorrectly banned, <a href="https://steam-rep.com/contact">contact us</a>.</p> </div> </div> <div class="faq-item faq-item-11"> <div class="title">A STAFF MEMBER FROM STEAM-REP MESSAGED ME, IS THIS REAL?</div> <div class="content"> <p>Staff members will NEVER contact you via Discord, reddit, Facebook, or any other platform that&#39;s not described here.</p> <p>Current staff list:</p> <ul class="staff-members"> <li><a href="https://steamcommunity.com/profiles/76561197964285909" target="_blank">j.Fry</a></li> </ul> </div> </div> <div class="faq-item faq-item-12"> <div class="title">HOW DO I CONTACT YOU FOR BUSINESS PURPOSES?</div> <div class="content"> <p>You can send an email at business@steam-rep.com .</p> </div> </div></div>', 2);
sg.render = function(e, t, r, a, n, o) {
    const i = ta("Footer");
    return ha(), fa("div", lg, [cg, wa(i)])
};
var ug = {
    components: {
        Footer: Md
    }
};
const dg = {
        id: "subpage-changelog",
        class: "subpage"
    },
    hg = ka('<div class="heading-wrapper"><div class="heading">CHANGELOG</div><div class="brief">Read about site changes and new additions. The list is updated on each new version of the site.</div></div><div class="changelog"><div class="update"><div class="title">Update 12/22/2020</div><div class="changes"><ul><li>â€¢ Added small staff note when staff edits a feedback</li><li>â€¢ Added option to save your email </li><li>â€¢ Added option to delete recently written feedback (option available for 30 minutes only)</li><li>â€¢ Added timestamps to feedback</li><li>â€¢ Added button to Steamrep on user profiles</li><li>â€¢ Menu automatically closes when selecting an option on mobile</li><li>â€¢ FAQ updated</li><li>â€¢ Fixed names breaking with specific characters (such as &quot;&gt;&quot;)</li><li>â€¢ No longer possible to report yourself</li><li>â€¢ Fixed user reports not asking for contact email</li><li>â€¢ Fixed feedback reports</li><li>â€¢ Added missing $ symbol in trade value</li><li>â€¢ Centered Steam log in button on mobile</li><li>â€¢ Fixed incorrect transaction text when trade value was not specified</li><li>â€¢ Fixed multiple visual bugs on desktop and mobile</li></ul></div></div></div>', 2);
ug.render = function(e, t, r, a, n, o) {
    const i = ta("Footer");
    return ha(), fa("div", dg, [hg, wa(i)])
};
const {
    data: pg,
    logged: fg
} = mc, {
    email: mg
} = pg;
var vg = {
    components: {
        Input: qc,
        Footer: Md
    },
    data: () => ({
        disabled: !1,
        validator: new nc("user", "email", {
            email: mg
        })
    }),
    setup() {
        const {
            addNotify: e
        } = bc;
        return {
            addNotify: e
        }
    },
    beforeRouteEnter(e, t, r) {
        r((e => {
            e.from = t
        }))
    },
    methods: {
        async handleSubmit() {
            try {
                if (this.disabled) return void this.addNotify({
                    title: "Cooldown...",
                    type: "warning"
                });
                this.disabled = !0;
                const e = this.validator.validate();
                this.validator.force();
                let t = null;
                e && (t = await uc("user", "email", this.validator.data)), e && t ? (this.addNotify({
                    title: "Form accepted!",
                    content: "Your form was submitted successfully!",
                    type: "success"
                }), mc.data.session.email = this.validator.data.email, await this.$router.push(fc.value)) : this.addNotify({
                    title: "Fix the form",
                    type: "error"
                })
            } catch (e) {
                2001 === e.error && this.addNotify({
                    title: "Cooldown...",
                    type: "warning"
                })
            } finally {
                setTimeout((() => {
                    this.disabled = !1
                }), 5e3)
            }
        }
    }
};
const gg = {
        id: "subpage-email",
        class: "subpage"
    },
    yg = {
        class: "email-wrapper"
    },
    bg = {
        class: "enter-email"
    },
    wg = wa("h1", null, "We need your mail so we can contact you later about anything related to your feedbacks or reports. Your address will not be visible to other users.", -1),
    Eg = wa("span", {
        class: "text"
    }, "Save", -1),
    Pg = wa("span", {
        class: "icon"
    }, [wa("img", {
        src: "/icon/send.svg"
    })], -1);
vg.render = function(e, t, r, a, n, o) {
    const i = ta("Input"),
        s = ta("Footer");
    return ha(), fa("div", gg, [wa("div", yg, [wa("div", bg, [wg, wa(i, {
        name: "email",
        validator: n.validator,
        placeholder: "Your e-mail address"
    }, null, 8, ["validator"]), wa("button", {
        class: ["btn btn-blue hvr-bounce-to-right", {
            disabled: n.disabled || !n.validator.valid
        }],
        onClick: t[1] || (t[1] = (...e) => o.handleSubmit && o.handleSubmit(...e))
    }, [Eg, Pg], 2)])]), wa(s)])
};
var kg = {
    components: {
        Footer: Md
    }
};
const _g = {
        id: "subpage-page_error",
        className: "subpage"
    },
    Sg = wa("div", {
        class: "page-error"
    }, [wa("img", {
        src: "/icon/500.svg"
    })], -1);
kg.render = function(e, t, r, a, n, o) {
    const i = ta("Footer");
    return ha(), fa("div", _g, [Sg, wa(i)])
};
const Cg = function(e) {
    const t = vi(e.routes, e);
    let r = e.parseQuery || ji,
        a = e.stringifyQuery || Ui,
        n = e.history;
    const o = qi(),
        i = qi(),
        s = qi(),
        l = tt(ai, !0);
    let c = ai;
    Ro && e.scrollBehavior && "scrollRestoration" in history && (history.scrollRestoration = "manual");
    const u = $o.bind(null, (e => "" + e)),
        d = $o.bind(null, Ni),
        h = $o.bind(null, Ii);

    function p(e, o) {
        if (o = Fo({}, o || l.value), "string" == typeof e) {
            let a = Lo(r, e, o.path),
                i = t.resolve({
                    path: a.path
                }, o),
                s = n.createHref(a.fullPath);
            return Fo(a, i, {
                params: h(i.params),
                hash: Ii(a.hash),
                redirectedFrom: void 0,
                href: s
            })
        }
        let i;
        "path" in e ? i = Fo({}, e, {
            path: Lo(r, e.path, o.path).path
        }) : (i = Fo({}, e, {
            params: d(e.params)
        }), o.params = d(o.params));
        let s = t.resolve(i, o);
        const c = e.hash || "";
        s.params = u(h(s.params));
        const p = function(e, t) {
            let r = t.query ? e(t.query) : "";
            return t.path + (r && "?") + r + (t.hash || "")
        }(a, Fo({}, e, {
            hash: (f = c, Mi(f).replace(Ri, "{").replace($i, "}").replace(Di, "^")),
            path: s.path
        }));
        var f;
        let m = n.createHref(p);
        return Fo({
            fullPath: p,
            hash: c,
            query: a === Ui ? Hi(e.query) : e.query
        }, s, {
            redirectedFrom: void 0,
            href: m
        })
    }

    function f(e) {
        return "string" == typeof e ? {
            path: e
        } : Fo({}, e)
    }

    function m(e, t) {
        if (c !== e) return si(8, {
            from: t,
            to: e
        })
    }

    function v(e) {
        return y(e)
    }

    function g(e) {
        const t = e.matched[e.matched.length - 1];
        if (t && t.redirect) {
            const {
                redirect: r
            } = t;
            let a = f("function" == typeof r ? r(e) : r);
            return Fo({
                query: e.query,
                hash: e.hash,
                params: e.params
            }, a)
        }
    }

    function y(e, t) {
        const r = c = p(e),
            n = l.value,
            o = e.state,
            i = e.force,
            s = !0 === e.replace,
            u = g(r);
        if (u) return y(Fo(u, {
            state: o,
            force: i,
            replace: s
        }), t || r);
        const d = r;
        let h;
        return d.redirectedFrom = t, !i && function(e, t, r) {
            let a = t.matched.length - 1,
                n = r.matched.length - 1;
            return a > -1 && a === n && Io(t.matched[a], r.matched[n]) && jo(t.params, r.params) && e(t.query) === e(r.query) && t.hash === r.hash
        }(a, n, r) && (h = si(16, {
            to: d,
            from: n
        }), O(n, n, !0, !1)), (h ? Promise.resolve(h) : w(d, n)).catch((e => li(e) ? e : x(e))).then((e => {
            if (e) {
                if (li(e, 2)) return y(Fo(f(e.to), {
                    state: o,
                    force: i,
                    replace: s
                }), t || d)
            } else e = P(d, n, !0, s, o);
            return E(d, n, e), e
        }))
    }

    function b(e, t) {
        const r = m(e, t);
        return r ? Promise.reject(r) : Promise.resolve()
    }

    function w(e, t) {
        let r;
        const [a, n, s] = function(e, t) {
            const r = [],
                a = [],
                n = [],
                o = Math.max(t.matched.length, e.matched.length);
            for (let i = 0; i < o; i++) {
                const o = t.matched[i];
                o && (e.matched.indexOf(o) < 0 ? r.push(o) : a.push(o));
                const s = e.matched[i];
                s && t.matched.indexOf(s) < 0 && n.push(s)
            }
            return [r, a, n]
        }(e, t);
        r = Bi(a.reverse(), "beforeRouteLeave", e, t);
        for (const n of a) n.leaveGuards.forEach((a => {
            r.push(Yi(a, e, t))
        }));
        const l = b.bind(null, e, t);
        return r.push(l), ss(r).then((() => {
            r = [];
            for (const a of o.list()) r.push(Yi(a, e, t));
            return r.push(l), ss(r)
        })).then((() => {
            r = Bi(n, "beforeRouteUpdate", e, t);
            for (const a of n) a.updateGuards.forEach((a => {
                r.push(Yi(a, e, t))
            }));
            return r.push(l), ss(r)
        })).then((() => {
            r = [];
            for (const a of e.matched)
                if (a.beforeEnter && t.matched.indexOf(a) < 0)
                    if (Array.isArray(a.beforeEnter))
                        for (const n of a.beforeEnter) r.push(Yi(n, e, t));
                    else r.push(Yi(a.beforeEnter, e, t));
            return r.push(l), ss(r)
        })).then((() => (e.matched.forEach((e => e.enterCallbacks = {})), r = Bi(s, "beforeRouteEnter", e, t), r.push(l), ss(r)))).then((() => {
            r = [];
            for (const a of i.list()) r.push(Yi(a, e, t));
            return r.push(l), ss(r)
        })).catch((e => li(e, 8) ? e : Promise.reject(e)))
    }

    function E(e, t, r) {
        for (const a of s.list()) a(e, t, r)
    }

    function P(e, t, r, a, o) {
        const i = m(e, t);
        if (i) return i;
        const s = t === ai,
            c = Ro ? history.state : {};
        r && (a || s ? n.replace(e.fullPath, Fo({
            scroll: s && c && c.scroll
        }, o)) : n.push(e.fullPath, o)), l.value = e, O(e, t, r, s), D()
    }
    let k;

    function _() {
        k = n.listen(((e, t, r) => {
            let a = p(e);
            const o = g(a);
            if (o) return void y(Fo(o, {
                replace: !0
            }), a).catch(Ao);
            c = a;
            const i = l.value;
            var s, u;
            Ro && (s = Ko(i.fullPath, r.delta), u = Qo(), Jo.set(s, u)), w(a, i).catch((e => li(e, 12) ? e : li(e, 2) ? (r.delta && n.go(-r.delta, !1), y(e.to, a).catch(Ao), Promise.reject()) : (r.delta && n.go(-r.delta, !1), x(e)))).then((e => {
                (e = e || P(a, i, !1)) && r.delta && n.go(-r.delta, !1), E(a, i, e)
            })).catch(Ao)
        }))
    }
    let S, C = qi(),
        T = qi();

    function x(e) {
        return D(e), T.list().forEach((t => t(e))), Promise.reject(e)
    }

    function D(e) {
        S || (S = !0, _(), C.list().forEach((([t, r]) => e ? r(e) : t())), C.reset())
    }

    function O(t, r, a, n) {
        const {
            scrollBehavior: o
        } = e;
        if (!Ro || !o) return Promise.resolve();
        let i = !a && function(e) {
            const t = Jo.get(e);
            return Jo.delete(e), t
        }(Ko(t.fullPath, 0)) || (n || !a) && history.state && history.state.scroll || null;
        return kt().then((() => o(t, r, i))).then((e => e && Go(e))).catch(x)
    }
    const R = e => n.go(e);
    let F;
    const $ = new Set;
    return {
        currentRoute: l,
        addRoute: function(e, r) {
            let a, n;
            return ri(e) ? (a = t.getRecordMatcher(e), n = r) : n = e, t.addRoute(n, a)
        },
        removeRoute: function(e) {
            let r = t.getRecordMatcher(e);
            r && t.removeRoute(r)
        },
        hasRoute: function(e) {
            return !!t.getRecordMatcher(e)
        },
        getRoutes: function() {
            return t.getRoutes().map((e => e.record))
        },
        resolve: p,
        options: e,
        push: v,
        replace: function(e) {
            return v(Fo(f(e), {
                replace: !0
            }))
        },
        go: R,
        back: () => R(-1),
        forward: () => R(1),
        beforeEach: o.add,
        beforeResolve: i.add,
        afterEach: s.add,
        onError: T.add,
        isReady: function() {
            return S && l.value !== ai ? Promise.resolve() : new Promise(((e, t) => {
                C.add([e, t])
            }))
        },
        install(e) {
            e.component("RouterLink", Vi), e.component("RouterView", Gi), e.config.globalProperties.$router = this, Object.defineProperty(e.config.globalProperties, "$route", {
                get: () => rt(l)
            }), Ro && !F && l.value === ai && (F = !0, v(n.location).catch((e => {})));
            const t = {};
            for (let e in ai) t[e] = Ja((() => l.value[e]));
            e.provide(xo, this), e.provide(Do, Be(t)), e.provide(Oo, l);
            let r = e.unmount;
            $.add(e), e.unmount = function() {
                $.delete(e), $.size < 1 && (k(), l.value = ai, F = !1, S = !1), r.call(this, arguments)
            }
        }
    }
}({
    history: function(e) {
        const t = ti(e = Vo(e)),
            r = function(e, t, r, a) {
                let n = [],
                    o = [],
                    i = null;
                const s = ({
                    state: o
                }) => {
                    const s = Zo(e, location),
                        l = r.value,
                        c = t.value;
                    let u = 0;
                    if (o) {
                        if (r.value = s, t.value = o, i && i === l) return void(i = null);
                        u = c ? o.position - c.position : 0
                    } else a(s);
                    n.forEach((e => {
                        e(r.value, l, {
                            delta: u,
                            type: qo.pop,
                            direction: u ? u > 0 ? Bo.forward : Bo.back : Bo.unknown
                        })
                    }))
                };

                function l() {
                    const {
                        history: e
                    } = window;
                    e.state && e.replaceState(Fo({}, e.state, {
                        scroll: Qo()
                    }), "")
                }
                return window.addEventListener("popstate", s), window.addEventListener("beforeunload", l), {
                    pauseListeners: function() {
                        i = r.value
                    },
                    listen: function(e) {
                        n.push(e);
                        const t = () => {
                            const t = n.indexOf(e);
                            t > -1 && n.splice(t, 1)
                        };
                        return o.push(t), t
                    },
                    destroy: function() {
                        for (const e of o) e();
                        o = [], window.removeEventListener("popstate", s), window.removeEventListener("beforeunload", l)
                    }
                }
            }(e, t.state, t.location, t.replace),
            a = Fo({
                location: "",
                base: e,
                go: function(e, t = !0) {
                    t || r.pauseListeners(), history.go(e)
                },
                createHref: Xo.bind(null, e)
            }, t, r);
        return Object.defineProperty(a, "location", {
            get: () => t.location.value
        }), Object.defineProperty(a, "state", {
            get: () => t.state.value
        }), a
    }(),
    routes: [{
        path: "/",
        component: Xd
    }, {
        path: "/profile",
        component: $h,
        meta: {
            login: !0
        }
    }, {
        path: "/profile/:steam_id",
        component: $h
    }, {
        path: "/login",
        component: ag
    }, {
        path: "/report-user",
        component: Ov,
        meta: {
            login: !0,
            email: !0
        }
    }, {
        path: "/contact",
        component: Vh
    }, {
        path: "/settings",
        component: up,
        meta: {
            login: !0
        }
    }, {
        path: "/feedback",
        component: Fp,
        meta: {
            login: !0
        }
    }, {
        path: "/feedback/:steam_id",
        component: Fp,
        meta: {
            login: !0
        }
    }, {
        path: "/faq",
        component: sg
    }, {
        path: "/changelog",
        component: ug
    }, {
        path: "/logout",
        component: $h,
        meta: {
            login: !0
        }
    }, {
        path: "/:pathMatch(.*)*",
        name: "NotFound",
        component: Xd
    }, {
        path: "/email",
        component: vg,
        meta: {
            login: !0
        }
    }, {
        path: "/500",
        component: kg
    }]
});
Cg.beforeEach((e => (["/login", "/logout", "/email"].includes(e.path) || (fc.value = e.path), e.meta.login && !mc.logged.value ? "/login" : !(e.meta.email && !mc.data.session.email) || "/email")));
const Tg = ((...e) => {
    const t = (zn || (zn = zr(Vn))).createApp(...e),
        {
            mount: r
        } = t;
    return t.mount = e => {
        const a = function(e) {
            if (x(e)) {
                return document.querySelector(e)
            }
            return e
        }(e);
        if (!a) return;
        const n = t._component;
        T(n) || n.render || n.template || (n.template = a.innerHTML), a.innerHTML = "";
        const o = r(a);
        return a.removeAttribute("v-cloak"), a.setAttribute("data-v-app", ""), o
    }, t
})(Fc).use(Cg).use(ko);
Tg.config.globalProperties.$callApi = uc, Tg.mount("#app");